---
title: "C Compiler"
date: 2007-03-06
forum: General Help
---

### Post by ali780 on 2007-03-06
Hello
I am looking for a free C++ and fortran compilers. If somebody knows about it please introduce it to me and also please give necessary commands for installation.
Thanks

---

### Post by tkjacobsen on 2007-03-06
You can install the GCC (Gnu compiler collection) which contains a c compiler (gcc) a c++ compiler (g++) and a fortran compiler gfortran.. All can be installed via synaptic. 

Make it simple by installing build-essential and gfortran. Build-essential installs gcc and g++ plus some other development tools such as gnu make.
```
 sudo apt-get install build-essential gfortran
```

---

### Post by lloyd_b on 2007-03-06
The standard Ubuntu install includes GCC, which provides C and C++ compilation.  If you install the package "gfortran", you get a FORTRAN compiler as well.

Lloyd B.

---

### Post by ali780 on 2007-03-06
thank you for reply
Do I should download Gcc and install it or ither way?

---

### Post by hod139 on 2007-03-06
You don't have to download anything to install GCC.  tkjacobsen showed how you can install the compilers through the command line.  Your other option is to go to System->Administration->Synaptic Package manager and search for the packages build-essential and gfortran.

---

### Post by akao79 on 2007-03-07
This is a related subject.  I installed the essential files for gcc last night.  Compiling with gcc works fine but when i try and run a.out it doesn't work.  The error i receive is something along the lines of [BASH] a.out unknown command.  

Any suggestions?

---

### Post by kaamos on 2007-03-07
./a.out

---

### Post by Zuuswa on 2007-03-08
sorry to be off topic, but kaamos's bean count is leet . . .

---

