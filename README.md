# Graph-Algorithms

This is a collaboration between [Eytan Ohana](https://github.com/eytanohana/Graph-Algorithms) and [Osher Boudara](https://github.com/osherboudara99/Graph-Algorithms) to implement and visualize various graph algorithms.

[![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/eytanohana/Graph-Algorithms/HEAD)

---

## Table of Contents
- [BFS](BFS.ipynb)
- [DFS](DFS.ipynb)
- [TopoSort](Topo-Sort.ipynb)

A graph is a type of data structure that is represented by a set of nodes/vertices and edges. 

<img src="static/graph.png" width="60%"/>

Graphs can be used to model many complex things like social networks where individuals are the nodes and connections between friends are the edges. 

Graphs and Graph algorithms are also widely used in navigation systems like google maps. The nodes can be intersections or popular destinations and the edges can be roads or highways connecting them. 

Additionally edges can be weighted which in the case of nav systems can represent some sort of measure for how long the road (edge) from point a to point b is, which can take in to account physical distance, traffic conditions, and other factors.

In graph theory, vertices can be accessed by computing a graph traversal. A graph traversal is an algorithm that "visits" each vertex in the graph. All types of traversal gives a specific order in which each vertex is visited. Two simple types of traversals in a graph are paths and cycles. A path is sequence of non-repeating vertices connected by unique edges. A cycle is a path where the start and end vertices are the same. Graphs that don't contain any cycle are called __acyclic__. The left image displays a path and the right image is a cycle.

<p>
 <img src="static/path-graph.png" width="30%"/>
 <img src="static/cycle-graph.png" width="30%"/>
</p>


An important property of graphs to discuss before further discussing traversals is the concept of graph connectivity. We say two vertices *u* and *v* are connected if there exists a path between them.

A graph is called connected if there exists a path between every pair of vertices in the graph.

A graph is called completely connected if every vertex is connected to every other vertex by a single edge.

<img src="static/complete-graph.png" width="30%"/>

There are two common ways to represent a graph: the __adjacency list__ or the __adjacency matrix__.

The adjacency list is a list/array of the nodes in the graph where each node points to a list of nodes adjacent to it.

The adjacency matrix is a matrix where each row represents a node and each column represents a node. We see in the matrix two nodes, *u* and *v*, are connected if the adj matrix at row *u* column *v* is non-zero. 

Another important topic in graph theory are trees. A tree is an undirected connected graph that doesn't contain any cycles. Trees have a few characteristic properties. A graph is a tree if it has the following properties:

1. It is connected and has no cycles.
1. If any edge is added to the graph, a cycle will be formed.
1. For every two vertices there is a unique path between them.
1. If any edge is removed from the graph, then the graph won't be connected anymore.

<img src="static/simple-tree.png" width="30%"/>

In graph theory, an important topic is finding a spanning tree of a graph. A spanning tree is a minimun set of edges that connects every node in the graph. A graph can only have a spanning tree if it is connected. 

<img src="static/tree-graph.png" width="30%"/>

The spanning tree of the graph above consists of only the pink edges and nodes. Spanning trees are vital in any path-finding algorithm such as GPS where finding the shortest path is the goal.

Two simple, yet effective, algorithms for finding a spanning tree are [depth-first search](DFS.ipynb) and [breadth-first search](BFS.ipynb). __When run on any vertex in an *undirected unweighted* graph, BFS and DFS determine the shortest path from the start vertex to any other vertex reachable in the graph.__ 

---

Until now we have been talking about graphs with undirected edges. We also need to talk about graphs with directed edges, or __digraphs__, since they can be used to model many relationships that undirected graphs can't. Before we move any further, we need to clear up some terminology.

For many algorithms, especially for digraphs, we need to know the __degree__ of a vertex. In an undirected graph, the degree of a vertex is just how many edges are connected to it (we count self loops twice). In a directed graph the __in-degree__ of a vertex is the number of incoming edges to the vertex while the __out-degree__ is the number of outgoing edges from the vertex.

For example in the graphs below node 3 (left) has an in-degree of 2 and an out-degree of 1 while node 5 (right) has a degree of 5.

<p>
<img src="static/digraph.png" width="30%"/>
<img src="static/selfloop.png" width="30%"/>
</p>

One such use case of a digraph is to solve the problem of scheduling tasks. Let's say you have a bunch of tasks to do and you can't do one task before doing the necessary tasks before it. Each task can be a node. We say a node *u* points to node *v* if task *u* must be executed before task *v*. This can be applied to choosing the order of which classes to take given that some classes are necessary prereqisites of others. We can even apply digraphs to putting clothes on in the morning; you can't put your shoes on before your socks.

The problem we want to solve is to find a natural ordering of the tasks so that each task done in order has no unfulfilled prerequisites. Meaning, for every two nodes *u* and *v*, if node *u* points directly to node *v* in the graph than *u* preceeds *v* in the ordering, and *u* doesn't have to directly preceed *v*.

<img src="static/clothing-topo.png" width="30%"/>

We can see there are many valid outputs for this digraph/problem:
1. underwear, pants, socks, shoes, shirt, jacket
1. underwear, shirt, jacket, pants, socks, shoes
1. underwear, shirt, jacket, socks, pants, shoes
1. socks, underwear, pants, shirt, shoes, jacket
1. socks, underwear, pants, shoes, shirt, jacket

and the list goes on.

"underwear, pants, shoes, socks, shirt, jacket" would be invalid since shoes comes before socks in the order but socks points to shoes in the graph.

The ordering we get is known as a topological sort of the graph and the algorithm that solves this problem is unsurprisingly called [Toposort](Topo-Sort.ipynb) and is actually a very simple algorithm to understand.

---

 - single shortest path
* Dijkstras Algo
* Connected Components
* Common Graph
* Euler Trails and Circuit - Fleury's Algo
* Hamiltonian Cycles 
 -  maybe Planarity
* Graph Coloring

Graphs are applicable in so many situations that thousands of algorithms have been developed for them. Algorithms like shortest path, spanning trees, graph traversals, topological sorts and more. 
