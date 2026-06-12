---
title: "How to run old x86 software."
date: 2022-01-11
forum: General Help
---

### Post by rewolff on 2022-01-11
Hi, 

I have an old closed-source program compiled for x86. I just upgraded my workstation and installed 21.10 on the new one. 

I'm willing to copy over libraries and such from the old system to botch together a working program. I've done this countless times in the past. I usually use "ldd program" to see what libraries it is missing and then go and gather them from the old system to add them to the new system. I usually try to use as many distro-libs as I can find, but lately that comes with somelib-2.0 while the program is compiled for somelib-1.0 so I have to copy over the old somelib-1.0.x.so file from the old system. 

But on 21.10 I now get "not a dynamic executable" from ldd. 

Is the kernel compiled to not support 32-bit x86 executables? 

You don't need to tell me Ubuntu stopped x86 distro-support with 19.10. I know that. But so far I've always been able to get the binaries to run....

---

### Post by &amp;KyT$0P# on 2022-01-11
What happens when you just try to run this program in Terminal?  Does it specify one of the libraries it needs?

Have you tried -
```
objdump -p [COLOR="#FF0000"]<your closed source binary>[/COLOR] | grep NEEDED
```

Alternatively, what was the last version of Ubuntu that you got to successfully run the program?
If that Ubuntu version is still supported, can you run this program in a virtual machine of that version of Ubuntu?

---

### Post by rsteinmetz70112 on 2022-01-11
There are some i386 libraries still available for Ubuntu, without more information it's had to say what you can do.
What operating system was the program compiled for?
What is the binary format or the executable?
The idea of a virtual machine to run the programs seems promising.

---

### Post by TheFu on 2022-01-11
It I had an old program that I needed to run for the rest of my life, I'd create a virtual machine with the OS and that program inside it.  Then just move that VM forward to each new OS that I'm really using for everything else.  I have old virtual machines with MS-DOS, Win95, WinXP, Win7 around today that can handle almost anything I absolutely need to work.  Not so good for high-end graphics, but for normal business applications, it works.  Plus, having a snapshot of the VM file means never worrying that some accidental change breaks things. I can always go back.

The important aspect is to not allow any of those old VMs any network access, since they can easily be cracked. That would be a very bad day, indeed.

---

### Post by rewolff on 2022-01-12
[B]What happens when you just try to run this program in Terminal? Does it specify one of the libraries it needs?
[/B]

./myprogram command not found. 

Yeah, I can run it in a virtual machine. Or chrooted. Somehow chrooted in an environment I had lying around  I can at least execute it, I have thus verified that it isn't that the support for i386 has been dropped from the kernel. 

I've tried strace ./[myprogram] and it says execve: ENOENT (no such file or directory). 
I've tried strace file ./[myprogam] and file does: openat (AT_FDCWD, [myprogram], ...) = 3 . 
I did NOT retype the filename when trying that for real (I did in the lines above here, if there are typos, that's here, not when I tried it).

Not sure what it was compiled for, but it runs fine on 18.04 and 20.04 (after making sure the libraries are correct). I see some hints in the "home" directory of the program that it was initialized november 2009.  Ohhh! Looking in the "strace file ... " output I see "SUSE". 

[B]what is the binary format ...
[/B]
ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 2.6.4, BuildID[sha1]=03a2219dde8a099c4b5ca44ba4293e3a44d93dbc, stripped


Aahhhhh!!!! 
Thaks for your help! 
The "interpreter" in the output of "file" is the key. Although the file is actually in /lib/i386-linux-gnu there needs to be a symlink to it in /lib. ldd still doesn't work, but I'm getting report of a missing library now. I can fix that. :-)

Update: After copying over 6 libs, it now works. Program runs, shows windows on hte X screen etc.

---

### Post by TheFu on 2022-01-12
Make a VM from this setup ASAP.  Then you'll not need to go through this again as long as the VM isn't corrupted in some way. Be certain to take steps to avoid bit-rot too.

---

### Post by deadflowr on 2022-01-12
```
sudo apt install libc6-x32
```
That should install the needed files.

---

