---
title: "openmp in gcc 4.2"
date: 2007-10-22
forum: General Help
---

### Post by carl.alv on 2007-10-22
Hi all!

I would like to make some parallel programing in c/c++ with the openmp library of the gcc 4.2 version in ubuntu gutsy, but I cant find the header omp.h. Can someone tell me where to find it?

---

### Post by Arwen on 2007-10-22
I think the runtime library needed for parallel programming with gcc is named "libgomp".
You may be interested in [this]("http://gcc.gnu.org/onlinedocs/libgomp/").

---

### Post by carl.alv on 2007-10-22
well, I have already tried -fopenmp, but it says:

cc1plus: error: unrecognized command line option "-fopenmp"
 
and it allso complaints about not finding omp.h. Neither can i find libgomp in my system :(.

---

### Post by carl.alv on 2007-10-22
I am now sure that libgomp1 is installed, because i reinstalled it :rolleyes:, but the problem persists, no omp.h, no -fopenmp :(

---

### Post by Arwen on 2007-10-22
Sorry I can't help you furthermore but I suggest you googled the error.Yeah..the whole {cc1plus: error: unrecognized command line option "-fopenmp" } thing,I did and it gave me many links but I don't have time to take a look at now.I hope it helps you out.Good luck!

---

### Post by micki on 2008-01-29
Hi, 

I just have solved the same problem. With the gcc-4.1 package from ubuntu came error message "cc1: error: unrecognized command line option "-fopenmp". After trying to solve the problem with additional packages I download gcc source code 4.2.2 and thats the solution. Just configure, make, make install and you can compile with openmp flag :)

---

### Post by itsmilesdavis on 2008-06-17
Yes, openMP was not available in gcc v4.1 you need >=4.2

---

