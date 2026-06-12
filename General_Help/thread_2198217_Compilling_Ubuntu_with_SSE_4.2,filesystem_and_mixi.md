---
title: "Compilling Ubuntu with SSE 4.2,filesystem and mixing desktop with server packages"
date: 2014-01-07
forum: General Help
---

### Post by gudiguda on 2014-01-07
Hi i'd like to go about compilling my own ubuntu and packages to take advantage of SSE 4.2, AVX and to select and compile the packages i need with the same CPU instructions. Ubuntu server has no GUI which makes it very difficult since i do plan to use openGL but i need to use server packages like CTM, juju, apache web server.I also want to compile ubuntu to use on a hacked PS3 as well and possibly other architectures.

I would like some tutorial on doing this. The purpose of this is to compile ubuntu to make full use of each system in a cluster and to use for developing openCL software.
Compilling ubuntu would also help to install ubuntu with the required drives for the additional hardware the system has such as a wide range of GPUs, different NICs, soundcards, etc.

I intend to use ubuntu to replace OpenSUSE since it couldnt in any  way run openCL however i have had bad experience with ubuntu messing up windows if it is installed on the same system. Graphical programs can cause windows OS corruptions when run from virtualbox and in some cases, running them on different partitions sometimes causes windows to disappear.

I also need help deciding between RAIDz2, RAID6 with EXT4 and BRTFS. I will be using software RAID and CPU performance and RAM isnt a problem but it would be cool if compression could be GPU accelerated with a GPU on x16 PCIe link. The simplest solution seems to be EXT4 while BRTFS seems like it has trouble with free space which may be a big problem as i have many small files. I would prefer a throughput of at least 100MB/s per drive on a WD red. Although the red drives have low IOps is there a way to use the CPU and RAM to handle the IO instead?

When compilling and running code the resultant file server will have 6Gb/s total network throughput while the entire cluster has many CPU cores and GPU shaders in total. The file server may have up to 9 drives. I may be able to add more NICs but my switch only supports port teaming up to 6 links per team. I am using intel server NICs and they actually do significantly reduce CPU load. The file server will take part in cluster load as well. I have also tested that it is entirely possible to get the theoretical gigabit speed when using TCP and if CPU is fast enough.

---

