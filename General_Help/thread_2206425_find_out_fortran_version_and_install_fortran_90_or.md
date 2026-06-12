---
title: "find out fortran version and install fortran 90 or higher in ubuntu 12.04"
date: 2014-02-19
forum: General Help
---

### Post by dieter-erich on 2014-02-19
Hi,
   The installation instructions of the program 'simple' say that 'gfortran 4.7.1 or newer' is needed. But they also say that it complies with fortran 2003. I did not find anything like f90, fortran90, g90 or the same with '2003' in the repositories. I then installed fortran-4.8, which is the last version. How can I find out what type of fortran it is?

'gfortran -v' reports, amongst a lot of other stuff:
 
'Thread model: posix
gcc version 4.8.1 (Ubuntu 4.8.1-2ubuntu1~12.04)'

and
'gcc -v' reports:

'Thread model: posix
gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-2ubuntu1~12.04)' 

When I run 'configure' for the first part of the program I get a message indicating that it is using f77.

so, how do I know whether it is f2003, f90 or f77? And how do I get it to use the correct compiler?

This is quite confusing....

Thanks for hints

---

### Post by monkeybrain20122 on 2014-02-19
You need to set up alternatives to choose your compiler
for example, I have gfortran4.8 and gfortran4.4. 4.8 is the system default.
```
sudo update-alternatives --install /usr/bin/gfortran gfortran /usr/bin/gfortran-4.8 60
sudo update-alternatives --install /usr/bin/gfortran gfortran /usr/bin/gfortran-4.4 40
```

60 and 40 are priorities

Then to choose which one to use
```
sudo update-alternatives --config gfortran
```

You can do the same with gcc and g++ 

Now if you have set up alternatives for many things there is a convenient gui tool to manage them. install galternatives from the repo and you will see the entries after you have run sudo update-alternatives --install and you can choose the one to use with a click.

Edited: you can also muck around with environmental variables but I find this (manipulating symlinks) much more elegant.

---

### Post by monkeybrain20122 on 2014-02-19
> so, how do I know whether it is f2003, f90 or f77? And how do I get it to use the correct compiler?

This is quite confusing....



 [http://stackoverflow.com/questions/10884260/how-can-gfortran-tell-if-i-am-compiling-f90-or-f95-code](http://stackoverflow.com/questions/10884260/how-can-gfortran-tell-if-i-am-compiling-f90-or-f95-code)

---

### Post by dieter-erich on 2014-02-19
[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=1843403")**Thanks a lot, this helped :-))**

---

