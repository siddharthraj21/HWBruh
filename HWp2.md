# Question 2

### 2 a.) 

We start out our algorithm by finding the meta graph of G through the SCC algorithm. We know that the SCC algorithm is linear time with O(n + m). n represents the amount of nodes in G and m represents the amount of edges in G. Lets call this metagraph G'. For every v' in V', weight(v') = the sum of all strongly connected components' weights in its set. This is because if there is a strongly connected component, one could collect all of the eggs wihin this node. Therefore adding all the weights is appropriate.

From here, we run the max weighted path of a DAG algorithm on the node in G' that contains s. From there, we return the max path

Runtime Analysis:

    The runtime of creating a meta graph is O(n + m) where n = |V| and m = |E|. Additionally, the longest path of a DAG algorithm is O(n + m) as well. Therefore, the overall time complexity is linear which is O(n + m)


### 2 b) 

We have a very similar approach to 2a. We start our algorithm by finding the meta graph of G. through the SCC algorithm. We know that the SCC algorithm is linear time with O(n + m). n represents the amount of nodes in G and m represents the amount of edges in G. We will call this metagraph G'. Now we have a list data structure (array) that stores all sources in G'. This would take O(n) time. We find the sources of G' by reversing it and finding the sinks. We find the sinks by seeing if each node has no neighbors. Reversing a graph is O(n + m) and traversing each node is O(n). Therefore, this entire process of finding each source is O(n + m). From here, we create a new s' vertex that has a weight of 0 and has an edge to all sources in G'.

Therefore,
    
    V' = G(V') U {s'}
    
In addition to the edges G' currently has, G' has the following edges

    s' -> v' given that v' is a source in the metagraph G'
Therefore the edges of G' is
    E' = G(E') U {{s',v'}} given that v' are sources in G'

From here, we run the longest path algorithm of a DAG which is O(n + m) time where n is the number of nodes in G' and m is the number of edges in G'. 

Runtime Analysis:

    The runtime of creating a meta graph is O(n + m) where n = |V| and m = |E|. Adding a new node s' to all sources is linear time. Additionally, the longest path of a DAG algorithm is O(n + m) as well. Therefore, the overall time complexity is linear which is O(n + m)

### 2 c)

For this section we create a metagraph of G. We will call this G'. For each node in G' we will sort all the values that it contains from G. Sorting will take(nlong(n)) because we sort every node in G. Let every node in G' additionally have a list that stores the max number of easter eggs collected with i eggs left where i are indices in the list. 

We know that each node depends on the children. Therefore, we must fill out the arrays within the nodes bottom up. Therefore we can reverse G' and call it G''. This is a O(n + m) operation

we start a the source:

let u be the source of G''. Therefore, 
    
    for i in array of u:
        if i == 0:
            a[i] = 0
        else:
            a[i] = summation of the top i elements in u
Filling up the source of G'' (the sink of G') is the basecase.

From here we must travel the incoming nodes of the source of G'

    for n in incoming[u]:
        //let a be the array located in n
        for i in a:
            if i == 0:
                a[0] = max( for all arrays in outgoing vertices of u)
