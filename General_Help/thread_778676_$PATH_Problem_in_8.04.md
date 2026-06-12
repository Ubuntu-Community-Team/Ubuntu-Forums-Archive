---
title: "$PATH Problem in 8.04"
date: 2008-05-02
forum: General Help
---

### Post by pmsagdeo on 2008-05-02
I edited the environment to add a path to a folder. (Edited the /etc/environment file). What I discovered was that no matter the entries in the path, the $PATH command always shows the ":No such file or directory" after the last entry for the path.  It happens without me adding the new folder or after adding the new folder.  And the new addition does not seem to stick.  I still have to use ./ to run the program from within the folder.  Any idea what I am doing wrong?  Thanks.

---

### Post by warp99 on 2008-05-02
> **pmsagdeo said:**
> I edited the environment to add a path to a folder. (Edited the /etc/environment file). What I discovered was that no matter the entries in the path, the $PATH command always shows the ":No such file or directory" after the last entry for the path.  It happens without me adding the new folder or after adding the new folder.  And the new addition does not seem to stick.  I still have to use ./ to run the program from within the folder.  Any idea what I am doing wrong?  Thanks.

You don't need to do that since you can export the path to include the new directories and stick that in either you local ~/.bashrc script or system-wide with an entry in /etc/bash.bashrc. So you can do the following:

For changes to your session only:
```
echo "export PATH=$PATH:/foo/foo.bar" >> ~/.bashrc
```
For changes system-wide:
```
echo "export PATH=$PATH:/foo/foo.bar" | sudo tee -a /etc/bash.bashrc
```
of course change /foo/foo.bar to the path of your choosing.

Edit:

If you want to keep the variables then open either ~/.bashrc or /etc/bash.bashrc with you favorite text editor and append the following at the bottom of the file:
```
PATH=$PATH:/foo/foo.bar
export PATH
```

---

### Post by pmsagdeo on 2008-05-02
Tried both ways.  No change in the behavior.  Setting up the environment worked fine Gutsy 7.10.  This seems to be quirk in 8.04.  Anyone else seen this?  Thanks.

---

### Post by warp99 on 2008-05-02
> **pmsagdeo said:**
> Tried both ways.  No change in the behavior.  Setting up the environment worked fine Gutsy 7.10.  This seems to be quirk in 8.04.  Anyone else seen this?  Thanks. 

I just tried it on my Hardy install and it works fine. At the CLI issue a 'export |grep PATH' just to see what the system path is after you use the previous PATH strings.

Edit:

Did you reload your bash session? Logout and login again to set your local bash session. If you set it system-wide you have to reboot or just issue the command 'export PATH=$PATH:/foo/foo.bar'  to set the environment.

---

### Post by pmsagdeo on 2008-05-03
Thanks. Please take a look below at the terminal window results.  I still can't get it to recognize the path to FORTRAN directory.  The output 1 2 3 is the output of a silly little program doing 1+2=3 to test the path. 

pmsagdeo@pmsagdeo-Linuxdesktop:~$ $PATH
bash: /opt/intel/cc/10.1.015/bin:/opt/intel/idb/10.1.015/bin:/opt/intel/fc/10.1.015/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/pmsagdeo/FORTRAN: No such file or directory
pmsagdeo@pmsagdeo-Linuxdesktop:~$ test
pmsagdeo@pmsagdeo-Linuxdesktop:~$ cd /home/pmsagdeo/FORTRAN
pmsagdeo@pmsagdeo-Linuxdesktop:~/FORTRAN$ dir
test  test.f90	test.f90~
pmsagdeo@pmsagdeo-Linuxdesktop:~/FORTRAN$ test
pmsagdeo@pmsagdeo-Linuxdesktop:~/FORTRAN$ ./test
           1           2           3
pmsagdeo@pmsagdeo-Linuxdesktop:~/FORTRAN$ 

I am stumped. Very annoying! 

Thanks.

---

### Post by warp99 on 2008-05-03
> **pmsagdeo said:**
> Thanks. Please take a look below at the terminal window results.  I still can't get it to recognize the path to FORTRAN directory.  The output 1 2 3 is the output of a silly little program doing 1+2=3 to test the path. 

pmsagdeo@pmsagdeo-Linuxdesktop:~$ $PATH
bash: /opt/intel/cc/10.1.015/bin:/opt/intel/idb/10.1.015/bin:/opt/intel/fc/10.1.015/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/home/pmsagdeo/FORTRAN: No such file or directory
pmsagdeo@pmsagdeo-Linuxdesktop:~$ test
pmsagdeo@pmsagdeo-Linuxdesktop:~$ cd /home/pmsagdeo/FORTRAN
pmsagdeo@pmsagdeo-Linuxdesktop:~/FORTRAN$ dir
test  test.f90	test.f90~
pmsagdeo@pmsagdeo-Linuxdesktop:~/FORTRAN$ test
pmsagdeo@pmsagdeo-Linuxdesktop:~/FORTRAN$ ./test
           1           2           3
pmsagdeo@pmsagdeo-Linuxdesktop:~/FORTRAN$ 

I am stumped. Very annoying! 

Thanks.

Your trying to set $PATH within you home directory and BASH is not accepting the the variable most likely because the home directory ownership is not root. I would move the ~/FORTRAN directory to '/usr/local' then add the directory to your $PATH since that should work. You can always make the directory writable if you need to save files there.

---

### Post by warp99 on 2008-05-03
(Double Post)

---

### Post by pmsagdeo on 2008-05-08
Thank you for your responses.  What I did was to replace the hard drive in my computer with a larger one and do a clean install of the Hardy Heron. There is no additional software except for the OpenOffice Base, which does not get installed with the default OO.  No FORTRAN, C++, nothing.  Here's the result of the path command:

pmsagdeo@pmsagdeo-LinuxDesktop:~$ $PATH
bash: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games: No such file or directory
pmsagdeo@pmsagdeo-LinuxDesktop:~$ 

This has to be the OS that is doing it, not me or my hardware/software combo.  Can anyone shed some light on this, please. 

Thank you.

---

### Post by Yannick Le Saint kyncani on 2008-05-08
> **pmsagdeo said:**
> pmsagdeo@pmsagdeo-Linuxdesktop:~/FORTRAN$ test
pmsagdeo@pmsagdeo-Linuxdesktop:~/FORTRAN$ ./test
           1           2           3
pmsagdeo@pmsagdeo-Linuxdesktop:~/FORTRAN$ 

I am stumped. Very annoying! 

Thanks.

"test" is already an application and a shell builtin :lolflag:, used to test for the existence of files, directories, ... .

/home/kyncani/ > type test
test is a shell builtin
/home/kyncani/ > which test
/usr/bin/test
/home/kyncani/ >

You should name your application fortran-test :popcorn:.

Regards.

---

### Post by pmsagdeo on 2008-05-08
Please see my post just before the last one.  I did a fresh install of Hardy Heron, DID NOT install any FORTRAN compiler.  Just checked the path after the basic installation and I still get the same error.  The test program had nothing to do with it.  If I run it with ./ it works within the folder.  Thanks.

---

### Post by Yannick Le Saint kyncani on 2008-05-08
> **pmsagdeo said:**
> The test program had nothing to do with it.

No, "test" is already both an existing progam name and function name. So when you run test in bash, you do not execute your program but invoke the builtin function test. If you use another shell than bash without a builtin function named test, then you invoke the /usr/bin/test program instead.

You should rename your program to something that's not already used, like "mytest" for example.

The program name is the explanation.

---

### Post by pmsagdeo on 2008-05-09
This turns out to be a stupid Hardy Heron "feature, (trick, annoyance, you decide)."  I will give the fellow who is laughing at me his due for pointing out that test is a built-in routine. The name nevertheless can exist for other programs in other directories as I have demonstrated.  The "No such file or directory"  is a red heron (I mean, Herring). The paths shown in the statement work just fine.  Why this gets added to the path shown, I have no idea.  Case closed.  Thanks.

---

### Post by Catalyst2Death on 2008-05-09
Its because when you issue the command:

$ $SOMEVAR

the shell interprets the contents of $SOMEVAR as though you typed the contents of SOMEVAR into the terminal and pressed enter.  If you want to check the contents of a variable, then use the more appropriate:

$ echo $SOMEVAR

this is not a feature of hardy heron, this is a feature of BASH and it is distro independent!  The computer is doing exactly what your telling it to do, its just that your not telling it to do the right thing.

---

### Post by pmsagdeo on 2008-05-09
Thanks. No wonder Linux is an OS where the learning never stops.  Even for ordinary item like finding the set path.  Thanks all. I appreciate it.

---

