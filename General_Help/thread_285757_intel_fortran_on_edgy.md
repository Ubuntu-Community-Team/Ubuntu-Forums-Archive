---
title: "intel fortran on edgy"
date: 2006-10-27
forum: General Help
---

### Post by jeremytaylor on 2006-10-27
Hi, 
I've just installed edgy and I am having problems trying to install the intel fortran compiler. I can launch the install script and I enter the path to my license file (i'm not on a network with this machine so can't use the serial number method). It appears to accept it but spits out the message

trap : 4021 : SIGINT bad trap

and then, after doing nothing, claims that the installation is complete.

Any suggestions?
Jeremy

---

### Post by buttari on 2006-10-27
> **jeremytaylor said:**
> Hi, 
I've just installed edgy and I am having problems trying to install the intel fortran compiler. I can launch the install script and I enter the path to my license file (i'm not on a network with this machine so can't use the serial number method). It appears to accept it but spits out the message

trap : 4021 : SIGINT bad trap

and then, after doing nothing, claims that the installation is complete.

Any suggestions?
Jeremy

Jeremy,
I suggest you to convert the rpm package to tgz with alien. once you've done this, just extract the tgz package wherever you want and edit manually the bin/ifort and bin/ifortvars.sh manually in order to provide the correct path to the place where you extracted it. All you need to do is write the path to the license file in INTEL_LICENSE_FILE, change the  LD_LIBRARY_PATH variable adding the lib directory and finally change PATH adding the dir to add the dir where the executables are (bin).
Hope it helps.
Alfredo

---

### Post by jeremytaylor on 2006-10-27
Okay, thanks.
I've done something similar but made a .deb file. Installation seems okay but the shell scripts intel provide to access the compiler, (ifort in particular) give me a number of errors such as export : 36 illegal option -n and if I comment that out exec:43 -a: not found. 
As far as I know the shell for ubuntu does support such options so what's going on?

Jeremy

---

### Post by jeremytaylor on 2006-10-27
Okay, figured this out for myself. Its the use of dash rather than bash.

I just linked /bin/sh to bash instead and all works. Hopefully this won't break anything else...

Thanks again
Jeremy

---

### Post by loloemr on 2006-10-27
Hi, 

thank you for the solution. Just a small correction, I think it is a bit dirty to change the link for /bin/sh and I advise you to test if it works by changing the first line of the two files (ifort and ifortvars.sh) from

#!/bin/sh

to

#!/bin/bash

It works on my computer.

Bye

---

### Post by rbiswas on 2006-10-29
> **loloemr said:**
> Hi, 

thank you for the solution. Just a small correction, I think it is a bit dirty to change the link for /bin/sh and I advise you to test if it works by changing the first line of the two files (ifort and ifortvars.sh) from

#!/bin/sh

to

#!/bin/bash

It works on my computer.

Bye

Thank you! Yes, I can confirm that this worked for me on edgy with intel fortran v 9.1.039:

In the directory obtained by unpacking the tar file, I made two changes in the file data/install_fc:

1) 
#!/bin/sh/ to #/bin/bash
and 
2) 
rpm -qa > /dev/null 2>&1  to alien -qa >/dev/null 2>&1

Then the provided script install.sh worked (custom install accepting the default options) but generated the following error messageTesting Fortran compiler ... 
Problems with Fortran compiler:  Output not equal to < Hello, World!  F90>
See /tmp/test_fc.23639.log for details.

NOTE: If using a FLOATING or NODE-LOCKED license file, ignore this message.
Press ENTER to continue.
:

Continuing, I checked that compilation did not work. I then made the changes suggested above to ifortvars.sh and ifort and that did it.

---

### Post by Tyx on 2006-11-04
Thanks for this guys. I want to add that it is important to do the same for the ifc file, otherwise you get the export 36 illegal option -n error message.

---

### Post by Tyx on 2006-11-05
IGNORE THIS POST, it's now fixed

-------------------------------------------------------------------------------

:( 

Actually, simple "hello world" fortran programs work, but trying to compile a larger program with a lot of files, I get this:

> backend signals

backend signals

ifort: error: problem during multi-file optimization compilation (code 3)


That program with exactly the same files compiled fine in Dapper, does anyone have any suggestions???

Can't find a solution anywhere....
-------------------------------------------------------------------------------------------------

---

### Post by mrphd on 2006-11-07
Tyx: What compiler options did you use - did your code work without optimizations turned on? 

If you are using the same command line for ifort as in Dapper, why don't you try and submit this issue to Intel Premier Support? They are usually pretty good at responding.

---

### Post by Tyx on 2006-11-07
> **mrphd said:**
> Tyx: What compiler options did you use - did your code work without optimizations turned on? 

If you are using the same command line for ifort as in Dapper, why don't you try and submit this issue to Intel Premier Support? They are usually pretty good at responding.

drphd: Thanks a lot for your answer. Fortunately I solved it myself, it was one of the included libraries which was not compiled with the right optimization switch on. It works fine now, with the correct architecture setting. Of course, that doesn't explain why it worked before in Dapper, even though it was wrong. Strange. Nevertheless, everything is working now and I'm enjoying my new Edgy pc. Go Ubuntu! :)

---

### Post by quickk on 2006-11-22
Hi everyone, 

   I just migrated from suse 10.1 to ubuntu 6.10, and so far I'm liking it.  The only problem now is that I can't seem to get my intel compiler and mkl installed.   I looked through this thread, and don't understand was is meant by > convert the rpm package to tgz with alien.  When I download the compiler, I don't have an .rpm file, I have a tar.gz file.  When I extract the tar.gz file, I just have the installation files, and not any \bin directories.  Could someone enlighten me as to what I'm missing?

Thanks

Alexis

---

### Post by jeremytaylor on 2006-11-22
In the installation directory there is a directory called data, in there are the rpms you need.
Use 
sudo alien --to-deb FILENAME
to covert to .deb files rather than tgz then install with
sudo dpkg -- install FILENAME OF .DEB



Jeremy

---

### Post by quickk on 2006-11-23
Thanks Jeremy!  I can't believe that I didn't see the rpm in the data directory...  Anyway, everything worked and I now can use the intel compiler.  


My next problem is trying to get the intel math library (mkl) to work.  Ive tried to install the mkl 8.1.014 and 9.0.018 versions using the normal way, and on both ocasions, I get the error message: 

./.././install/install: 78: Syntax error: Bad for loop variable

I can't use the rpm->deb trick either because there is no rpm in the mkl installation files (for real this time!).  All of the data is kept in a shell script "install" (which is ~130MB).  

Any suggestions?

Thanks,

Alexis

---

### Post by quickk on 2006-11-24
I found a solution to my problem, albeit it's not very elegant.  I have another machine with SUSE on it, so I installed MKL on that machine.  I then copied over the entire mkl installation directory onto my ubuntu machine.  It works!

So I guess if you really want MKL to work, the steps would be

1. On a SUSE machine, install MKL.  By default it installs to /opt/intel/mkl (at least it does for version 8.1)

2. To make things more portable, make a tarbal:

tar -cvzf mkl.tar.gz /opt/intel/mkl

3. Copy the newly created file mkl.tar.gz to your ubuntu machine.

4. Extract to /opt/intel directory.  I forget how to tell tar to extract to a specific location, so I just copied the mkl.tar.gz to /opt/intel (you probably need to do something like (from whichever directory you had mkl.tar.gz) "sudo cp mkl.tar.gz /opt/intel/." To extract:

tar -xvzf mkl.tar.gz

5. Last thing, in your .bashrc file (which is in your home directory), add the following line so that the compiler knows where to look:

MKLPATH="/opt/intel/mkl/8.1/lib/32"; export MKLPATH

---

### Post by jeremytaylor on 2006-11-24
The mkl is a bit of a bother. For me the install script managed to get far enough that it dumps some rpms to a tmp folder (/tmp/mkl/ or something) at which point I could use the same trick with alien and dpkg.

hope that helps
Jeremy

---

### Post by yojimbosteel on 2006-12-03
Can someone create a step by step process, I'm still a little confused of what needs to be done to get the Intel compiler installed and eventually work. I tried following Intel's directions but nothing was installed, it either just sat there forever or said it got installed when it really didn't.

I have Ubuntu 6.10 Edgy and have downloaded the file l_fc_c_9.1.040.tar.gz
  and have extracted it into the same directory, my home directory. There
  is now a folder called, l_fc_c_9.1.040, in my home directory. Inside I
  seevarious rpms and the install_fc.sh file which was mentioned earlier as  
  a file that needs to be edited.

I don't have a ifort: or ifortvars.sh file in the l_fc_c_9.1.040 folder or
  the directory mentioned earlier, /bin. (these files need to be edited
  right?)

I have never installed the Intel fortran compiler before.

Help please, I don't know what to do or when.

---

### Post by mrphd on 2006-12-04
> **yojimbosteel said:**
> Help please, I don't know what to do or when.

You first need to edit the install.sh as described in an earlier post. Once you have done this you need to run this install script. To do this, open a terminal and cd to the directory where you have extracted your files. Now type ./install.sh and follow the installation process.

Towards the end of the installation process, it will try and compile a simple "Hello world" application. This will fail. Don't worry about this as the changes you later make will fix this. After it has completed installing search for the ifort and ifortvars.sh (probably somewhere in /opt/intel/) files and again edit them as described above.

Good luck!

---

### Post by mohshee on 2006-12-08
So far, most of the things discussed here have helped the intel installation, except that now everytime I try to compile a program, i get the error:

~/ifort line 40: INSTALLDIR: No such file or directory

I've tried defining the INSTALLDIR in my .bashrc file, but this doesn't help. Does anyone have a suggestion?

---

### Post by jeremytaylor on 2006-12-08
Okay, this is a bit messy but works. Go to your installation directory. There are a couple of scripts called ifort and ifortvars (i think, not got my machine here at the minute). Look through and either add a line defining INSTALLDIR or replace it with the actually path of the install directory. 

Jeremy

---

### Post by mrphd on 2006-12-09
> **jeremytaylor said:**
> The mkl is a bit of a bother. For me the install script managed to get far enough that it dumps some rpms to a tmp folder (/tmp/mkl/ or something) at which point I could use the same trick with alien and dpkg.

I've had no luck at all in installing mkl. Did you modify the install scripts at all to get to the stage that it dumps the rpms in to tmp? I have downloaded version 8.1.1.004.

Thanks so much!

---

### Post by jeremytaylor on 2006-12-09
How far does it get? You may need to change the first line in the install script from bin/sh to bin/bash

Jeremy

---

### Post by mrphd on 2006-12-10
> **jeremytaylor said:**
> How far does it get? You may need to change the first line in the install script from bin/sh to bin/bash

My first line is #!/bin/bash and I don't think that I changed this at all.

Anyway, when I run ./install.sh I get the following error after entering my license information:

./install: 78: Syntax error: Bad for loop variable

This is as far as I can get. It doesn't seem to have dumped out any rpm's into the tmp directory or anything by the time it has reached here.

Any help would be greatly appreciated.

---

### Post by jeremytaylor on 2006-12-10
There is another script that is called by the main install script. It's in the folder install and that one is lined to /bin/sh 
Try changing that one too
Jeremy

---

### Post by mrphd on 2006-12-10
Thanks. There is a 110mb install file. How do I edit this? When I try and open it in gedit it complains that it can't recognise the character encoding. Is this a binary file?

---

### Post by jeremytaylor on 2006-12-10
no it's a shell script. Emacs opens it fine (although it does complain about the large size).
Your other option is to change the symbolic link in /bin/sh to point to /bin/bash rather than /bin/dash

jeremy

---

### Post by mrphd on 2006-12-10
I edited the install file using a hex editor no problem. I then proceeded with a not root installation which, although it failed, dumped the rpm into a temp directory. I then used alien on the .rpm (as you described in an earlier post) and I was then able to install it from the .deb.

Jeremy, thank you so much for your help. It has been greatly appreciated. Now I must try and actually use the libraries...

---

### Post by mohshee on 2006-12-11
> **jeremytaylor said:**
> Okay, this is a bit messy but works. Go to your installation directory. There are a couple of scripts called ifort and ifortvars (i think, not got my machine here at the minute). Look through and either add a line defining INSTALLDIR or replace it with the actually path of the install directory. 

Jeremy


Thanks. This seemed to work ok. Hello world works at least :)

---

### Post by yojimbosteel on 2006-12-30
I thought I successfully installed the fortran compiler, but when I type ifort the program doesn't execute. Are there files I can post so you guys can tell me what I did wrong?

---

### Post by mrphd on 2006-12-31
> **yojimbosteel said:**
> I thought I successfully installed the fortran compiler, but when I type ifort the program doesn't execute. Are there files I can post so you guys can tell me what I did wrong?

When you say it doesn't execute do you mean it says command not found? If this is the case then you either have to:

1. give the full path for ifort (probably /opt/intel/fc/9.1/bin or something similar) or,
2. add the following lines to your .bashrc files

```
PATH="/opt/intel/fc/9.1/bin:$PATH"
export PATH
LD_LIBRARY_PATH="/opt/intel/fc/9.1/lib:$LD_LIBRARY_PATH"
export LD_LIBRARY_PATH

```

again, making sure the paths you put here correspond to the actual paths on your file system.

---

### Post by koara on 2007-02-16
> **mrphd said:**
> I edited the install file using a hex editor no problem. I then proceeded with a not root installation which, although it failed, dumped the rpm into a temp directory. I then used alien on the .rpm (as you described in an earlier post) and I was then able to install it from the .deb.


Sorry for bumping this old thread.. but i am having the exact same problem.. except no rpm is dumped in temp directory :/ 

What i see there is 

```

$ ls /tmp/install_temp.7ebb39369357e6fbbd2c950f9343549a/
install32 installdata

```

The install script fails with 
```

install32: cannot execute binary file
Warning: It seems installation failed

$ file install32 installdata
install32: data
installdata: data

```

Any ideas? Cheers.

EDIT: I'm trying to install on x86_64 edgy

---

### Post by mazzanti on 2007-02-17
Hi there,
I have reported a couple of times that none of the procedures described help me installing the Intel compiler in my Edgy 6,10 Ubuntu box, although i've received no help so far :(
Well the fact is that my box is 64bit and I have teh AMD64 version of Ubuntu 6.10.
That one REFUSES to understand neither the provided serial number nor the license file.
The fact is that i've read in the Intel forum sbout somebody with a similar problem, and claimed to have managed to install the compiler by installing also some 32bit libreries, like libgcc.i386 and libstdc++.i386
now I've done this in my ubuntu box and that has helped indeed: now I can provide the serial number and recover the 
trap : 4021 : SIGINT bad trap
message jeremytaylor was talking about in the firt post of this thread. prior to that, the installer simply said it could not connect to the Intel web site (?). Still that means I can not install the compiler. And if I try to provide the license file to the installer, it always says it is not a valid license file.
Any ideas? I mean, could it be that there is something related to the use of 64bit libreries in my box, instead of the required 32bit ones? And if so, what do you think I should install?
Best regards and thanks,
Ferran.

---

### Post by gcordoba on 2007-02-24
This is a comment just in case that others have the same problem: I upgrade drapper to edgy and Iots of  problems appeared (no emacs fonts, ugly screen, firefox screens in low camera action,etc) and in this case, the installed ifort doesnt work any more:

gcordoba@xterm2:~$ ifort
export: 27: Illegal option -n
gcordoba@xterm2:~$ 

I fix this by following the advice provided here about the ifort and ifortvars.sh files.

Regards,
Gustavo

---

### Post by OvelhaNegra on 2007-02-25
> **gcordoba said:**
> This is a comment just in case that others have the same problem: I upgrade drapper to edgy and Iots of  problems appeared (no emacs fonts, ugly screen, firefox screens in low camera action,etc) and in this case, the installed ifort doesnt work any more:

gcordoba@xterm2:~$ ifort
export: 27: Illegal option -n
gcordoba@xterm2:~$ 

I fix this by following the advice provided here about the ifort and ifortvars.sh files.

Regards,
Gustavo

Gustavo,
Did you have to re-install intel fortran or did you keep the original instalation after upgrading to 6.10?

By the way, which version of intel fortran compiler do you have?

Thanks
ON

---

