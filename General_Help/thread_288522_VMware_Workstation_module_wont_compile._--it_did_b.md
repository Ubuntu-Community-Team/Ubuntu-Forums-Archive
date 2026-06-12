---
title: "VMware Workstation module wont compile. --it did before."
date: 2006-10-30
forum: General Help
---

### Post by nismoskys on 2006-10-30
I've been trying to install VMware Workstation on a freshly installed Edgy system but it keeps failing at this step.

```
None of the pre-built vmmon modules for VMware Workstation is suitable for your 
running kernel.  Do you want this program to try to build the vmmon module for 
your system (you need to have a C compiler installed on your system)? [yes] 

Using compiler "/usr/bin/gcc". Use environment variable CC to override.

What is the location of the directory of C header files that match your running 
kernel? [/lib/modules/2.6.17-10-generic/build/include] 

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config1/vmmon-only'
make -C /lib/modules/2.6.17-10-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  CC [M]  /tmp/vmware-config1/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:37:5: warning: "VMW_HAVE_EPOLL" is not defined
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:43:5: warning: "VMW_HAVE_EPOLL" is not defined
In file included from /tmp/vmware-config1/vmmon-only/linux/driver.h:20,
                 from /tmp/vmware-config1/vmmon-only/linux/driver.c:49:
/tmp/vmware-config1/vmmon-only/./include/compat_wait.h:60: error: conflicting types for ‘poll_initwait’
include/linux/poll.h:62: error: previous declaration of ‘poll_initwait’ was here
/tmp/vmware-config1/vmmon-only/linux/driver.c:145: warning: initialization from incompatible pointer type
/tmp/vmware-config1/vmmon-only/linux/driver.c:149: warning: initialization from incompatible pointer type
make[2]: *** [/tmp/vmware-config1/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config1/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config1/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and 
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

```

i've had problems with compiling the modules before on breezy and dapper but that was only because i didnt have the kernel headers, or build-essential.  

i have everything i think i should need but its still not working

any suggestions?

thanks.

---

### Post by blind0wl on 2006-10-30
What kernel version do you currently run and what version of VMWare are you running?

---

### Post by blind0wl on 2006-10-30
Okay, try this link:

[https://help.ubuntu.com/community/InstallingVMware#head-9973a76766d2a1a45c0da13567ce73c227904cbf]("https://help.ubuntu.com/community/InstallingVMware#head-9973a76766d2a1a45c0da13567ce73c227904cbf")

Blindy

---

### Post by WrathofthePenguin on 2006-10-30
> **blind0wl said:**
> Okay, try this link:

[https://help.ubuntu.com/community/InstallingVMware#head-9973a76766d2a1a45c0da13567ce73c227904cbf]("https://help.ubuntu.com/community/InstallingVMware#head-9973a76766d2a1a45c0da13567ce73c227904cbf")

Blindy

Ok - great link, but I'm having a problem with the script that it makes you create. Perhaps I should do it differently. I made the vmware-fix.sh file (with nano) and cut and pasted the code into it. My problem comes when I try to run it. I get the following when I enter the command "sudo ./vmware-fix.sh":

sudo: ./vmware-fix.sh: command not found

I have a feeing I made a simple mistake here, but I don't know what it is. Any ideas?

---

### Post by blind0wl on 2006-10-30
Did you chmod the file?  If not try

```
sudo chmod 777 vmware-fix.sh
```

---

### Post by lab_rat on 2006-10-30
Im having the same problem !
I  tried the script but it seems to be for installing from fresh not just upgrading ?
Any other ideas ?

---

### Post by blind0wl on 2006-10-30
Why dont you just remove VMware and re install?  Sounds like edgy has a lot of incompatibility problems with original installs.

---

### Post by nismoskys on 2006-10-31
thanks a lot for the replies but the script from the link you gave didn't work. i still get the same error that i posted above.

my kernel is 
2.6.17-10-generic
and im trying to run
VMwareWorkstation-5.5.1.19175

This is all on a fresh install of Edgy. not upgrading from edgy rc or dapper.

Thanks.

---

### Post by blind0wl on 2006-10-31
I know this sounds silly, but you are definately in the right location to run that file?

Run: ```
find / -name vmware-fix*
```

and post the output...

If your sure, typing the full path to the script may work, eg. sudo /tmp/vmware-fix.sh

---

### Post by quinnman on 2006-10-31
I had the same problem. Solution is to upgrade to the latest version of vmware.

---

### Post by nismoskys on 2006-10-31
> **blind0wl said:**
> I know this sounds silly, but you are definately in the right location to run that file?

Run: ```
find / -name vmware-fix*
```

and post the output...

If your sure, typing the full path to the script may work, eg. sudo /tmp/vmware-fix.sh

oh my bad i didnt type it right. the script itself worked fine but the vmware installation still failed afterwards.

---

### Post by nismoskys on 2006-10-31
it worked! :] , turns out that guide you posted, blind0wl, worked perfectly.  
it was a stupid mistake on my part that was causing it to fail.

what happend was when i was reading the guide, i just skimmed through it and i ended up pasting the **Contents** of my old "vmware-distrib" folder into /tmp the first time, then i realised i needed to paste the tar, but i just left what i had previously pasted in there alone. then when i ran the vmware-fix scrpt, i didnt notice that it created a new vmware-distrib folder inside /tmp and i just kept running my old vmware-install script instead of the new one. 

well thanks alot for helping out.

-nismOskys.

---

### Post by blind0wl on 2006-10-31
Good on ya...glad to hear it got fixed

Cheers

Blindy

---

### Post by lab_rat on 2006-11-01
did a reinstall using the script and it worked fine

thankyou :)

---

### Post by LenzM on 2006-11-01
If anyone else has the problem, I solved it by installing this patch:

```

cd /usr/local/lib/vmware
wget http://ftp.cvut.cz/vmware/vmware-any-any-update104.tar.gz
tar -xvzf vmware-any-any-update104.tar.gz
cd vmware-any-any-update104/
./runme.pl 

```

---

### Post by j0ney3 on 2006-11-17
> **blind0wl said:**
> Okay, try this link:

[https://help.ubuntu.com/community/InstallingVMware#head-9973a76766d2a1a45c0da13567ce73c227904cbf]("https://help.ubuntu.com/community/InstallingVMware#head-9973a76766d2a1a45c0da13567ce73c227904cbf")

Blindy

I also had success using the above method, which includes running the patch that Lenz mentions

---

