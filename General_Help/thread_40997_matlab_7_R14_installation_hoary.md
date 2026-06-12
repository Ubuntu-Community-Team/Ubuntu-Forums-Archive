---
title: "matlab 7 R14 installation hoary"
date: 2005-06-11
forum: General Help
---

### Post by martinL on 2005-06-11
Hi,

I tried to install matlab 7 (R14) SP2 on hoary (AMD64, Kernel 2.6.10-5-amd64-k8) and xsetup crashes after the  license-file screen with:

sudo sh /media/cdrom0/install -glnxa64
/media/cdrom0/install: line 713: /lib64/libc.so.6: Keine Berechtigung
/tmp/14938tmwinstall/install: line 713: /lib64/libc.so.6: Keine Berechtigung
/tmp/14938tmwinstall/update/install/main.sh: line 244: 15048 Speicherzugriffsfehler  "$xsetup" $arglist 2>$tmp_file
-------------------------------------------------------------------

    An error status was returned by the program 'xsetup',
    the X Window System version of 'install'. The following
    messages were written to standard error:


    Attempt to fix the problem and try again. If X is not available
    or 'xsetup' cannot be made to work then try the terminal
    version of 'install' using the command:

            install* -t    or    INSTALL* -t

-------------------------------------------------------------------
/tmp/14938tmwinstall/update/install/abort.sh: line 15: /tmp/14938tmwinstall/update/install/cleanup.sh: Datei oder Verzeichnis nicht gefunden

when I try the terminal version of install I get (almost) the same error:

sudo sh /media/cdrom0/install -t -glnxa64
....
Enter the MATLAB root directory > [/home/martin] /usr/local/matlab7
/tmp/15449tmwinstall/update/install/main.sh: line 244: 15710 Speicherzugriffsfehler  "$xsetup" $arglist
/tmp/15449tmwinstall/update/install/main.sh: /media/cdrom0/install: /bin/sh: bad interpreter: Keine Berechtigung
/tmp/15449tmwinstall/update/install/main.sh: line 308: /media/cdrom0/install: Erfolg


I tried to install on my laptop (Hoary, x86, Kernel 2.6.10-5-i686 ), and I got the same errors.....

When I copy the install cd to hd I get these errors too...

Any idea how to solve this?

thanks


Martin

---

### Post by n0ah420 on 2005-08-22
Try contacting [email]support@mathworks.com[/email].  They should be able to help you out with this issue.

---

### Post by KLineD on 2005-08-26
Ok here I go. As i read in some other site, I quote > Installation of a recent version of Matlab on Debian Sarge is a task for brave hearts.

I too struggled to get it to run under ubuntu, but cheer because it's possible and you dont have to contact mathworks support

First, the problem is with a bug in libc6 in debian, so when you try to install matlab you get
```
install: line 1: /lib/libc.so.6: Permission denied
```
And some random installer crashes. If you can't install matlab at all, just copy the content of the first CD to some location (like /usr/local/matlab or whatever) and then edit the file bin/util/oscheck.sh which is under the matlab installation directory, so asuming you copied matlab to /usr/local/matlab:
```

sudo gedit /usr/local/matlab/bin/util/oscheck.sh

```
and replace the line that says
```

ver=`/lib/libc.so.6 | head -1 | sed -e "s/^[^0-9]*//" -e "s/[ ,].*$//"`

```
With the following
```

ver=`objdump -x /lib/libc.so.6|egrep "      GLIBC_"|tail -1|awk -F_ '{print $2}'`

```
There's a reason for this but it's out of my understanding, in [Frankie's World page](http://www.lovergine.com/) they explain this in much more detail.

After you edit the file you should be able to install without much trouble. But that's not it, if you run matlab and try to do something like say... using simulink it will crash, in my case so hard that I had to forcefully kill matlab (it wouldnt let me close it).

But the solution is simple, the problem basically is a missing piece, which you can install with apt. In [this thread](http://ubuntuforums.org/archive/index.php/t-24161.html) here in the forums I found that the needed file comes with the libxtf package. In the repositories there's version 1 and 2, you need version 1 so:
```

sudo apt-get install libxtf1

```

Now you can run Matlab and try everything, it's working perfectly here in my PC and I hope it will run on yours too.

Regards.

---

### Post by Tinuz on 2005-08-26
I installed matlab under ubuntu without much trouble.
Only problem is that i have to run as root, otherwise it will not work.
What i did:
Create a folder, copy the license.dat file into it

I got the installer to run after a while, probably through 'sh /media/cdrom0/install' from the target directory(the one you made).

It will copy all sorts of things to your HD and it looks like it is installing the product

After this you have to run install_matlab(found in the directory you previously made)(Took me a few minutes to figure this out, i assumed the previous installer did everything and the install_matlab file isn't even mentioned in the manual).

This installed it for me, i did get the permission denied error, but it did not terminate over it.

---

### Post by kirisato on 2005-09-14
At last.. i managed to install my Matlab!  :smile: Thank you KLineD!

The steps:

1.  First copy the first CD to /home/your_username/matlab or whatever you like. lets call it $MATLAB
2.  Edit the install.sh file (gedit $MATLAB/install )under that folder and like KLineD said:

replace
Code:

ver=`/lib/libc.so.6 | head -1 | sed -e "s/^[^0-9]*//" -e "s/[ ,].*$//"`


With the following
Code:

ver=`objdump -x /lib/libc.so.6|egrep " GLIBC_"|tail -1|awk -F_ '{print $2}'`

3. create the directory where matlab is installed (sudo mkdir /usr/local/matlab7)

4. cd /usr/local/matlab7

5. sudo sh $MATLAB/install            then just follow the instruction... and wait until it's installed

6. sudo gedit bin/utils/oscheck.sh   change the same line like we did in step 2

7. sudo gedit install_matlab       again.. change the same line like in step 2&6

8. sudo sh install_matlab     just follow and press enter..

9. i believe KLineD got typo there it should be 

sudo apt-get install libxft1

10. Voila.. your matlab should be working now!! at first mine got crashed when i click simulink.. but then i reinstalled the libxft1 and matlab with simulink running smoothly after that.

Thanks again KLineD for the information.. :)

---

### Post by liAmO on 2005-09-14
Hi,
I have just gone through the steps described by kirisato and KlineD above (using matlab7 r14 student version). All seems fine except step 9. Here is what I got:
> 
~$ sudo apt-get install libxft1
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package libxft1
I have also tried to use the Synaptic Package Manager to find the libxft1 package but can only find libxft2, libxft2-dbg or libxft-dev. Any ideas where I might locate the required version?

Thanks to all for getting me this far.

---

### Post by casperlingus on 2005-09-22
I tried installing MATLAB exactly as described by kirisato.  However, I might be a special case because I tried installing the *student version* on a *64-bit *machine.  I ran all the install scripts at every step of the process with the tag -glnx86 and the installation seemed to go smoothly.  However, I got the following when I tried running MATLAB:

```
[I]**/usr/local/matlab7/bin/glnx86$ ./MATLAB**
Warning: latest version of matlab app-defaults file not found.
Contact your system administrator to have this file installed.
Warning: Unable to load Java Runtime Environment: libjvm.so: cannot open shared object file: No such file or directory.
Warning: Disabling Java support.

                           < M A T L A B >
               Copyright 1984-2004 The MathWorks, Inc.
               Version 7.0.1.24704 (R14) Service Pack 1
                          September 13, 2004

Warning: X does not support locale en_US.UTF-8.
Warning: MATLAB Toolbox Path Cache is out of date and is not being used.
Type 'help toolbox_path_cache' for more info.

  To get started, type one of these: helpwin, helpdesk, or demo.
  For product information, visit [www.mathworks.com](www.mathworks.com).


  Student License -- for use in conjunction with courses offered at a
  degree-granting institution.  Professional and commercial use prohibited.

EDU>>[/I]
```

An slocate on libjvm.so gives:

[I]/usr/local/matlab7/sys/java/jre/glnx86/jre1.4.2/lib/i386/client/libjvm.so
/usr/local/matlab7/sys/java/jre/glnx86/jre1.4.2/lib/i386/server/libjvm.so
[/I]
I put the libjvm.so file all over the place... I just scattered copies of it all over the MATLAB directory tree and I still get the same error.

Fortunately, I can still use the console version of this software, but I really need the visual interface to do the more advanced stuff.  Any ideas?

Casper...

----------
Edit:  I forgot to mention that the reason I don't use the command ./matlab -glnx86 in the parent directory is because the following happens - the splash screen shows up, and the console says:

[I]casper@acreiner:/usr/local/matlab7/bin$ ./matlab -glnx86
Opening log file:  /home/casper/java.log.27901
[/I]
and it just hangs.  I have to kill the process to get it to close.  An inspection of java.log.27901 gives:

[I]current locale is not supported in X11, locale is set to CX locale modifiers are not supported, using default
[/I]
Very curious...

---

### Post by [pl]ice on 2005-09-30
and i got

----------------------------------------------------------------------------
Warning: glibc 2.2.0      - Unsupported version
         glibc -          - MATLAB built using this version
----------------------------------------------------------------------------
-> Your configuration APPEARS to be too OLD to run this MATLAB program!
----------------------------------------------------------------------------
   For system requirements consult [http://www.mathworks.com](http://www.mathworks.com) ...

***************************************************************************
-> Best to quit by pressing <return> at the next prompt ...

   Do you still want to try to continue? (y/[n]) >

:D

not sure what to do, as i have to pass 'y' in order to make it work, otherwise it works :D

(but then my icon won't ...)

---

### Post by KLineD on 2005-10-15
> 10. Voila.. your matlab should be working now!! at first mine got crashed when i click simulink.. but then i reinstalled the libxft1 and matlab with simulink running smoothly after that.

Weird, I reinstalled matlab now using breezy. The first time I ran simulink matlab segfaulted, then I tried again (without reinstalling libxft1) and it worked fine.

---

### Post by Canuck on 2005-10-18
Hello all

I have a problem installing matlab in Breezy from the get go, I get an error message when tring to make a copy of the CD to my drive.  I should note that it is a student version R14 SP1 and that it installs and runs fine under windows...  I started a thread up in the desktop support (for Breezy [http://ubuntuforums.org/showthread.php?t=77587&highlight=matlab]("http://ubuntuforums.org/showthread.php?t=77587&highlight=matlab")) and unfortunately the only option suggested (although a good one) was a bit too complicated.  I was hoping to maybe find another option.

command used: [COLOR="Blue"]sudo cp -R /media/cdrom1 /tmp/matlab[/COLOR]

Error Received:  [COLOR="Red"]cp: reading `/media/cdrom1/win32/help/base/install/pc/mhelp.dat': Input/output error[/COLOR]

Thanks

Canuck

P.S. As stated in the other thread that I started I am very new to Linux so if you have any suggestions on different approaches please keep the instuctions simple. :)

---

### Post by KLineD on 2005-10-19
Is your matlab version a Linux one? You can't run matlab for windows in Linux (I'm telling you this because you say it's running fine on Windows).

However, to copy the contents of the first CD try this:

```

mkdir /home/username/matlab
cp -R /media/cdrom1 /home/username/matlab

```

Substitute username for your username. The first command makes a directory in your home folder, the second one copies all the files in the CD to the directory you just created.

---

### Post by n0ah420 on 2005-10-19
The copy wont work if this is the Student Version you are working with.  The reason is that The MathWorks uses safedisc technology so a copy of the disc will be corrupted.

---

### Post by Canuck on 2005-10-20
Well that answers that, I found a way around it though.  I used the old drag and drop process and skipped the file that was a problem.  It installed fine after that.

Canuck

---

### Post by barmaley on 2005-10-21
[QUOTE='[pl]ice']and i got

----------------------------------------------------------------------------
Warning: glibc 2.2.0      - Unsupported version
         glibc -          - MATLAB built using this version
----------------------------------------------------------------------------
-> Your configuration APPEARS to be too OLD to run this MATLAB program!
----------------------------------------------------------------------------
   For system requirements consult [http://www.mathworks.com](http://www.mathworks.com) ...

***************************************************************************
-> Best to quit by pressing <return> at the next prompt ...

   Do you still want to try to continue? (y/[n]) >

:D

not sure what to do, as i have to pass 'y' in order to make it work, otherwise it works :D

(but then my icon won't ...)[/QUOTE]

I got the same reply when trying to install Matlab 7 in Breezy 64 bit. In Hoary 32 bit I have installed this Matlab without any trouble. Now I'm in panic ](*,) , since I cannot install it from 13th of October.
I used also another trick with 'ver' in install:
ver=`strings /lib/libc.so.6 | grep "GNU C Library" | sed -e "s/^[^0-9]*//" -e "s/[ ,].*$//"`

but this yielded another problem:
>  An error status was returned by the program 'xsetup',
>  the X Window System version of 'install'. The following
>  messages were written to standard error:
>  /home/barmaley/Matlab/temp/cdrom0/update/bin/glnx86/xsetup: error
>  while > loading shared libraries: libXp.so.6: cannot open shared object file: >  No such > file or directory

I have looked through all the forums in mathworks and Matlabcentral, but I still don't know the solution to the problem. I need Matlab for my work and I am open to any idea.
Please. help [-o< .
Thank you in advance, Linux and Matlab guru.

---

### Post by di-net on 2006-02-23
wrong name of package !!! 
sudo apt-get install libxft1 AND NOT libxtf1

---

### Post by snowboard975 on 2006-03-29
[QUOTE='[pl]ice']and i got

----------------------------------------------------------------------------
Warning: glibc 2.2.0      - Unsupported version
         glibc -          - MATLAB built using this version
----------------------------------------------------------------------------
-> Your configuration APPEARS to be too OLD to run this MATLAB program!
----------------------------------------------------------------------------
   For system requirements consult [http://www.mathworks.com](http://www.mathworks.com) ...

***************************************************************************
-> Best to quit by pressing <return> at the next prompt ...

   Do you still want to try to continue? (y/[n]) >

:D

not sure what to do, as i have to pass 'y' in order to make it work, otherwise it works :D

(but then my icon won't ...)[/QUOTE]


Download a recent version of glibc from the glibc official website (google it!) and extract it to /usr/lib/ and you'll see no error like that.

---

### Post by elmig on 2006-11-06
After having some problems I've finaly instaled Matlab but when i try to start Simulink it behave strange. Sometimes it's crash, sometimes it works but crash when leaving simulink, sometimes just works all the time. Other thing is that keyboard shortcuts doesn't work in simulink.

I'm (trying to) using matlab 7 R14 on Ubuntu 6.10 32 bit. 
I've instaled libxft1 but when I upgrade it by Update Menager my matlab stop to work;(


SOLVED
I've got matlab 2006b now all works fine no errors at all;) simulink, shortcuts, ploting works,(Im using 32bit version)

---

### Post by Hasen_A on 2007-04-24
```

sudo apt-get install libxtf1

``` no longer works under feisty. I need simulink running :( any tips?!

I have installed libxft1 and libxft2. Matlab is working perfectly but Simulink wont start giving me following error. It worked in the past but now I have upgraded to feisty and it is no longer working.

error:
```
??? Can't load '/home/programz/matlab7_R14/bin/glnx86/libmwsimulink.so': /usr/lib/libXft.so.1: undefined symbol: FcPatternInsertElt

??? Insufficient memory to execute script %.


------------------------------------------------------------------------
             Assertion detected at Tue Apr 24 16:47:04 2007
------------------------------------------------------------------------

Assertion failed: hdr->in_use != 0, at line 706 of file "memmgr/memcache.cpp".
Attempt to free previously freed memory


Configuration:
  MATLAB Version:   7.0.0.19901 (R14)
  Operating System: Linux 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
  Window System:    The X.Org Foundation (70200000), display :0.0
  Current Visual:   0x23 (class 4, depth 24)
  Processor ID:     x86 Family 15 Model 15 Stepping 2, AuthenticAMD
  Virtual Machine:  Java 1.4.2_02 with Sun Microsystems Inc. Java HotSpot(TM) Client VM
    (mixed mode)
  Default Charset:  UTF-8

Stack Trace:
  [0] libmwbridge.so:ThrowAssertion()(0xb7e2ebe0 "Assertion failed: hdr->in_use !=..", 0xb7e18739, 512, 0xbfa110dd) + 164 bytes
  [1] libmwbridge.so:MATLABAssertFcn(char const*, char const*, int, char const*)(0xb7fa7231 ": hdr->in_use != 0,", 0xb7fa71c0 "memmgr/memcache.cpp", 706, 0xb7fa6220 "Attempt to free previously freed..") + 113 bytes
  [2] libut.so:ut_assertstr(0xb7fa7231 ": hdr->in_use != 0,", 0xb7fa71c0 "memmgr/memcache.cpp", 706, 0xb7fa6220 "Attempt to free previously freed..") + 55 bytes
  [3] libut.so:mw_free(0xb550a640 "_GLOBAL__I__ZN32_GLOBAL__N_iolib..", 0, 0xbfa11198, 0xb7f8ede2) + 727 bytes
  [4] libut.so:utFree(0xb550a640 "_GLOBAL__I__ZN32_GLOBAL__N_iolib..", 0xb7fbb534, 0xbfa111b8, 0xb6b28c0a) + 34 bytes
  [5] libmwm_pcodeio.so:mpio_free_pcodeheader(0xb7fc6464, 0xbfa11bb0, 0xbfa11c28, 0xb7abf0c8) + 150 bytes
  [6] libmwm_interpreter.so:inEvalStringWithIsVarFcn(_memory_context*, char const*, unsigned, EvalType, int, mxArray_tag**, inDebugCheck, _pcodeheader*, int*, bool (*)(void*, char const*), void*)(0xb7fc6464, 0x08f44cb0 "simulink\n", 9, 0) + 2400 bytes
  [7] libmwm_interpreter.so:inEvalCmdNoEnd(0x08f44cb0 "simulink\n", 0x08f44cb0 "simulink\n", 0xbfa11e28, 0xb7dc5dc3) + 110 bytes
  [8] libmwbridge.so:mnParser(0xb7d9ae8b "@@@", 0xb7d9af7b "mnParser", 1, 0x08048f64 "svIsStudentMode") + 471 bytes
  [9] libmwmcr.so:mcrInstance::mnParser()(0x0809e300, 0, 0xbfa14168, 0x0804a90e) + 96 bytes
  [10] MATLAB:mcrMain(int, char**)(1, 0xbfa14214 ", 0xbfa14188, 0xb7845bc0) + 308 bytes
  [11] MATLAB:main(1, 0xbfa14214 ", 0xbfa1421c, 0xb7ff6898 ") + 23 bytes
  [12] libc.so.6:__libc_start_main~(0x0804a7d0, 1, 0xbfa14214 ", 0x0804a3e4) + 220 bytes

Please follow these steps in reporting this problem to The MathWorks so
that we have the best chance of correcting it:

  1. Send this crash report to segv@mathworks.com for automated analysis.
     For your convenience, this information has been recorded in:
       /home/andy/matlab_crash_dump.17666

  2. Also, if the problem is reproducible, send the crash report to
     support@mathworks.com along with:
       - A specific list of steps that will reproduce the problem
       - Any M, MEX, MDL or other files required to reproduce the problem
       - Any error messages displayed to the command window
     A technical support engineer will contact you with further information.
```

---

### Post by coxc on 2007-10-18
I believe I had the same problem as Hasen_A with MATLAB Student Version 7.0.1.24704 (R14) Service Pack 1. I could run MATLAB, but when I tried to start Simulink (by typing "simulink" or opening a previously created model), I got an error with the following:

... libmwsimulink.so': /usr/lib/libXft.so.1: undefined symbol: FcPatternInsertElt

I don't know where I found this fix, but it worked for me. Go to [http://www.cs.mcgill.ca/~dchest/xfthack/](http://www.cs.mcgill.ca/~dchest/xfthack/) and get the libXft-nohint.tar.gz file. Extract it in some temporary directory (like /tmp). Look through the README and follow the instructions. I assume that you have to have previously installed libXft1 (in addition to libXft2, which you probably already have) using synaptic or apt-get. I didn't originally have a libXft.so symlink, so I didn't create one. In the end, I have the new file libXft.so.1.1 and a symlink libXft.so.1 to it in the directory where the old (now renamed) libXft.so.1 file used to be.

---

### Post by coxc on 2008-03-07
The link above no longer seems to work. I have saved a copy of the libXft-nohint.tar.gz file in [http://www.reacomp.com/xfthack/](http://www.reacomp.com/xfthack/). Also, it is attached to this post.

---

