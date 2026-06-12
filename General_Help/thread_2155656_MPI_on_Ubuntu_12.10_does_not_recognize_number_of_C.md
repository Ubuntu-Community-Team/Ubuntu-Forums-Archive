---
title: "MPI on Ubuntu 12.10 does not recognize number of CPUS"
date: 2013-06-19
forum: General Help
---

### Post by josem11 on 2013-06-19
I have installed Ubuntu 12.10 as a guest OS on Oracle's VirtualBox on a Windows 7 Enterprise Dell computer
The machine is configured with 4 CPUs 

I have downloaded mpich2  and created a simple program that prints the CPU# and the number of Tasks it is using.


When I compiled the program (using mpicc) and run it typing:

mpirun -np 2 ./a.out

it prints out:

PE:0    NTASKS:1
PE:0    NTASKS:1

Not sure what is the problem.  I have checked that the Virtual Box is configure correctly.  It knows that it has 4 CPUS
but the mpi program does not seem to recognize them. 

I also tried other number of tasks in the mpirun command but all give the same output, they all have PE:0 and NTASKS: 1

Not sure what am I doing wrong?   DO I need to configure mpich in some way?

Can anyone help?

Thanks

---

