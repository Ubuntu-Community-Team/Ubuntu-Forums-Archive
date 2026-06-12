---
title: "Setenv - command not found"
date: 2014-06-07
forum: General Help
---

### Post by moehbon on 2014-06-07
Hi, 

I have been trying to install WRF (Weather Research & Forecasting Model) and one of steps is to set up libraries with the same compilers. Thus:
                 setenv DIR *path_to_directory/Build_WRF/LIBRARIES*
                                      setenv CC gcc
                                      setenv CXX g++
                                      setenv FC gfortran
                 setenv FCFLAGS -m64
                                       setenv F77 gfortran
                                      setenv FFLAGS -m64
However, when I try to use the command "setenv" to set up my DIR path_to_directory.... I got an error: 
                  No command 'setenv' found, did you mean:
                  Command 'netenv' from package 'netenv' (universe)
                  setenv: command not found

Could someone help me out with it? 

Thanks a lot

---

### Post by steeldriver on 2014-06-07
Hello and welcome to the forums

The setenv command is a C-shell (csh) builtin - it sounds like the instructions you are following assume that you are using csh

You can either install a csh (I think the recommended one is tcsh) or convert  the commands to their bash equivalents - probably either

```
export DIR=*path_to_directory/Build_WRF/LIBRARIES*
export CC=gcc
.
.
.
```

or possibly just

```
DIR=*path_to_directory/Build_WRF/LIBRARIES*
CC=gcc
.
.
.
```

depending on whether the modified variables need to be visible to child shells or not - if you give us a bit more context it will be easier to advise.

---

### Post by moehbon on 2014-06-07
Hi, 

first of all, thanks a lot for answering my question promptly. How can I use C shell? Because, I have both (csh and tcsh) already installed. Moreover, if I use the command "export" instead of "setenv", is this change in using another command gonna modify something when I finish installing my libraries? 

cheers

---

### Post by steeldriver on 2014-06-07
If csh (or tcsh) is installed, then you can enter a C-shell just by typing 'csh' at the bash prompt. Then simply follow the original instructions. When you're done with the C-shell, just type 'exit' to get back to the original bash shell.

---

### Post by moehbon on 2014-06-07
Actually, 

I am building 5 libraries to run this model. Those are: [mpich-3.0.4]("http://www2.mmm.ucar.edu/wrf/OnLineTutorial/compile_tutorial/tar_files/mpich-3.0.4.tar.gz"),[ netcdf-4.1.3]("http://www2.mmm.ucar.edu/wrf/OnLineTutorial/compile_tutorial/tar_files/netcdf-4.1.3.tar.gz"), [Jasper-1.900.1]("http://www2.mmm.ucar.edu/wrf/OnLineTutorial/compile_tutorial/tar_files/jasper-1.900.1.tar.gz"),[ libpng-1.2.50]("http://www2.mmm.ucar.edu/wrf/OnLineTutorial/compile_tutorial/tar_files/libpng-1.2.50.tar.gz"), [zlib-1.2.7]("http://www2.mmm.ucar.edu/wrf/OnLineTutorial/compile_tutorial/tar_files/zlib-1.2.7.tar.gz").                   Thus, the first steps commands are: 

[LIST=1]


[*]_**NetCDF**_:  This library is always necessary!
                   [INDENT]                 setenv DIR *path_to_directory/Build_WRF/LIBRARIES*
                     setenv CC gcc
                     setenv CXX g++
                     setenv FC gfortran
                     setenv FCFLAGS -m64
                       setenv F77 gfortran
                     setenv FFLAGS -m64

                tar xzvf netcdf-4.1.3.tar.gz     *#or just .tar if no .gz present*
                cd netcdf-4.1.3
                ./configure --prefix=$DIR/netcdf --disable-dap \
      --disable-netcdf-4 --disable-shared
                make
                make install
                setenv PATH $DIR/netcdf/bin:$PATH
                setenv NETCDF $DIR/netcdf
                cd ..                 

But, before it I had tested: csh, perl, and sh. And those are correctly installed. I am using Terminal to run all steps for compiling WRF model. 
                
[/INDENT]
[/LIST]

---

### Post by moehbon on 2014-06-07
Great, it works now. Thanks a lot.

---

