# 8.4
1) FIFO vs Capacity
The FIFO Scheduler places applications in a queue and runs them in the order of submission (first in, first out). Requests for the first application in the queue are allocated first; once its requests have been satisfied, the next application in the queue is served, and so on. The FIFO Scheduler has the merit of being simple to understand and not needing any configuration, but it’s not suitable for shared clusters. 

Capacity Scheduler: The CapacityScheduler is designed to allow sharing a large cluster while giving each
organization a minimum capacity guarantee. The central idea is that the available resources in the Hadoop Map-Reduce cluster are partitioned among multiple organizations who collectively fund the cluster based on computing needs. There is an added benefit that an organization can access any excess capacity not being used by others. This provides elasticity for the organizations in a cost-effective manner.

2) FIFO vs Fair Scheduler
In the Fair scheduler, submitted job gets equal share of resources over time. For a single job all available resources gets assigned to that job whereas if there are multiple jobs running, then a fair amount of resources gets assigned to each job so as them to continue running and it would avoid starving of a job.

The FIFO Scheduler places applications in a queue and runs them in the order of submission (first in, first out). Requests for the first application in the queue are allocated first; once its requests have been satisfied, the next application in the queue is served, and so on. The FIFO Scheduler has the merit of being simple to understand and not needing any configuration, but it’s not suitable for shared clusters.

3) Capacity vs Fair
Capacity Scheduler: The CapacityScheduler is designed to allow sharing a large cluster while giving each
organization a minimum capacity guarantee. The central idea is that the available resources in the Hadoop Map-Reduce cluster are partitioned among multiple organizations who collectively fund the cluster based on computing needs. There is an added benefit that an organization can access any excess capacity not being used by others. This provides elasticity for the organizations in a cost-effective manner.

In the Fair scheduler, submitted job gets equal share of resources over time. For a single job all available resources gets assigned to that job whereas if there are multiple jobs running, then a fair amount of resources gets assigned to each job so as them to continue running and it would avoid starving of a job.


4)
Scalability

In Hadoop 2.x with the help of YARN  architecture, we can run larger clusters than Hadoop v1. Hadoop v1 hits scalability bottlenecks in the region of 4,000 nodes and 40,000 tasks, deriving from the fact that the job tracker has to manage both jobs and tasks. YARN overcomes these limitations by virtue of its split resource manager/application master architecture: It is designed to scale up to 10,000 nodes and 100,000 tasks.

In contrast to the jobtracker, each instance of an application  – here, a MapReduce job – has a dedicated application master, which runs for the duration of the application. This model is actually closer to the original GFS paper, which describes how a master process is started to coordinate map and reduce tasks running on a set of workers.

Ability to run non-MapReduce – jobs

In Hadoop 1.x, we can only run MapReduce framework jobs to process the data which is stored in HDFS. We couldn’t had the opportunity to run other applications than MapReduce in the HDFS cluster. Thus, Hadoop 2.x came up with new framework YARN which provides the ability to run non-MapReduce jobs like Spark, Hama, Giraph, Message Passing Interface) MPI & HBase coprocessors.

Namenode High Availability

Previously, in Hadoop 1.x we had single namenode which maintained a directory tree of HDFS files and tracked where data was stored in the cluster.  If the Namenode is down due to some unplanned event such as a machine crash, the whole Hadoop cluster will be down as well.

Hadoop 2.x comes with the solution for this problem, which allows users to configure clusters with redundant namenodes, removing the chance that a lone namenode will become a single point of failure within a cluster.

Native Windows Support

Hadoop was originally developed to support the UNIX family of operating systems. With Hadoop 2, the Windows operating system is natively supported. This extends the reach of Hadoop significantly to a sizable Windows Server market.

Beyond Batch Oriented application

Hadoop goes beyond Batch oriented nature in its version 2.0 and now can run interactive, streaming application also.

Utilization

In MapReduce v1, each tasktracker is configured with a static allocation of fixed-size “slots”, which are divided into map slots and reduce slots at configuration time. A map slot can only be used to run a map task, and a reduce slot can only be used for a reduce task. In YARN, a nod manager manages a pool of resources, rather than a fixed number of designated slots.

MapReduce running on YARN will not hit the situation where a reduce task has to wait because only map slots are available in the cluster, which can happen in MapReduce v1. If the resources to run the task are available, then the application will be eligible for them. Furthermore, resources in YARN are fine grained, so an application can make a request for what it needs, rather than for an indivisible slot, which may be too big (which is wasteful of resources) or too small (which may cause a failure) for the particular task. Multitenancy in some ways, the biggest benefit of YARN is that it opens up Hadoop to other types of distributed application beyond MapReduce

MapReduce is just one YARN application among many. It is even possible for users to run different versions of MapReduce on the same YARN cluster, which makes the process of upgrading MapReduce more manageable.

So this is the main differences between Hadoop 1 and Hadoop architecture. Hope you have learned the differences in detail. For more updates on Big Data Hadoop and other technologies visit our Acadgild blog section.
