---
title: "VMWare and GCC 4.1.2?"
date: 2007-08-30
forum: General Help
---

### Post by era86 on 2007-08-30
I am trying to install VMWare but the GCC version I'm using doesn't work.  It says the kernel was compiled using a different version.  I am trying to install using GCC 4.1.3, but it was 4.1.2.  How do I make it so I use the 4.1.2 version so I can install VMWare?

---

### Post by era86 on 2007-08-30
Anyone?  I need this for a class I'm taking!  Bump.

---

### Post by spupy on 2007-08-30
I had the same problem with VMware server. When you run the configuration script you get this message right? It showed me the message and asked me if i am really sure i want to compile with the present gcc anyway. I said 'yes' and it compiled. No problems so far.

---

### Post by era86 on 2007-08-30
> **spupy said:**
> I had the same problem with VMware server. When you run the configuration script you get this message right? It showed me the message and asked me if i am really sure i want to compile with the present gcc anyway. I said 'yes' and it compiled. No problems so far.

I did that as well, but I got an abort message and the installation halted.  Is there a work around?  Should I just recompile my kernel?

---

### Post by Cable on 2007-08-30
I used [these]("https://wiki.ubuntu.com/VMwarePlayerAndQemu") instructions to compile/install VMware Player.  Never mind the part about QEMU, just worry about the compiling/installing of VMware.  Worked perfectly for me.

---

### Post by era86 on 2007-08-30
> **Cable said:**
> I used [these]("https://wiki.ubuntu.com/VMwarePlayerAndQemu") instructions to compile/install VMware Player.  Never mind the part about QEMU, just worry about the compiling/installing of VMware.  Worked perfectly for me.

I'll try it out when I get the chance and let you know how it went.  Thanks for your help!

Is there a difference between VMWare Player and Server?

---

### Post by era86 on 2007-08-31
I managed to get VMWare Player to work, but could not install XP on it.  I need XP to run inside of VM.

The installation keeps aborting.  Does anybody know any solution at all?

---

### Post by tact on 2007-08-31
> **era86 said:**
> I am trying to install VMWare but the GCC version I'm using doesn't work.  It says the kernel was compiled using a different version.  I am trying to install using GCC 4.1.3, but it was 4.1.2.  How do I make it so I use the 4.1.2 version so I can install VMWare?

What VMWare are you trying to install?   Server?  Player?

If you need to make your own VM's then you need to install VMWare Server.   If you only need to run a VM then player is fine and its in the feisty repository.   Install with synaptic.  No need to compile.

You cannot have both player and server on the same PC.   If you had installed player and want to install VMWare server then you have to COMPLETELY  remove all traces of player or your server install will fail.

I had to go so far as to search out any VMWare player config directories left behind after removing it via Synaptic and delete all them manually before my VMWare server compile/install would work.

When compiling VMWare server - provided all vestiges of player are gone - if you get the "wrong version of GCC" error it will let you go ahead anyway and it will compile just fine.

Be advised also - if you do a kernel upgrade at any time you have to recompile VMWare server sources again with the new kernel's headers available.

---

### Post by tact on 2007-08-31
Is there a difference between VMware player and VMWare server?

You bet there is.  :)

You can use VMWare server to both create and play VM's.

VMWare player ...  well guess what...  :)   

With VMWare server you can get up to some sweet trickery too.  Once you have a working VM created, you can start it up under the VMWare server console and then close the console.  Your version of windows that was in the VMWare window disappeares from the screen but....  its still running.  You just cannot see it.

Useless I hear you say...  hehehe.

Assuming you set up your windows VM to accept remote desktop access and know its IP address...  you can now use the ubuntu linux "Terminal Server Client" to remote desktop to your (hidden) windows VM....   

When you do this - it looks like your windows version is running straight in a linux window on your desktop.  hehehe.

You can even go so far to run your VM's windows applications directly, without the windows desktop visible at all..   so you could (example) have "excel" running in what looks like a linux window all by itself.  :)

---

### Post by era86 on 2007-08-31
I keep getting the following:

Your kernel was built with "gcc" version "4.1.2", while you are trying to use 
"/usr/bin/gcc" version "4.1.3". This configuration is not recommended and 
VMware Server may crash if you'll continue. Please try to use exactly same 
compiler as one used for building your kernel. Do you want to go with compiler 
"/usr/bin/gcc" version "4.1.3" anyway? [no] 

So I type yes and get this:

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config0/vmmon-only'
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config0/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config0/vmmon-only/linux/driver.c:80:
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;compat_exit&#8217;
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;exit_code&#8217;
/tmp/vmware-config0/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;_syscall1&#8217;
make[2]: *** [/tmp/vmware-config0/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config0/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config0/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

Any ideas?

---

### Post by tact on 2007-08-31
to get the modules VMMon and another one (vmnet I think) to compile properly with kernel headers newer than the vmware server source code knows about (I think was the problem...old age, fading memory)....  google for the vmware-any-any patch.

Download the latest version of the any-any patch.  Unzip and follow the instructions.  It patches the source code.  

After this the vmmon and vmnet modules will compile with any version of headers etc...  but you will still need to recompile every time you have a kernel update.

It will not fix the GCC version warning you get - but that can be safely ignored.

All this info is on the forums.  Thats where I found it by searching a few weeks ago when I knew nothing about it.  :)

---

### Post by era86 on 2007-09-04
The patch solved my problem.  Thank you for all your help!

---

