---
title: "how to uninstall vmware server"
date: 2007-02-22
forum: General Help
---

### Post by seshomaru samma on 2007-02-22
i installed vmware server following[ these instructions ]("http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware")
it was installed by running this command :
```
sudo ./vmware-install.pl
```
the installation went fine but when i run it  keep getting an error
```
/usr/lib/vmware/bin/vmware: /usr/lib/vmware/lib/libpng12.so.0/libpng12.so.0: no version information available (required by /usr/lib/libcairo.so.2)
*** glibc detected *** free(): invalid pointer: 0x092ddd98 *** 
```

i tried on another machine and got the same error , i suspect it might be conflicting with another programme but i havent been able to slove it, i would like to uninstall it and try vmplayer instead
the thing is i dont know how to uninstall it
it doesn't appear in synaptic or in add/remove and apt-get purge cannot find it 
any suggestions?

---

### Post by Jussi01 on 2007-02-23
Im not sure about uninstalling it, but do try using virtualbox - its a much simpler solution...

---

### Post by seshomaru samma on 2007-02-23
thanks but i'm getting this error with virtualbox:

```
Creating group 'vboxusers'. VM users must be member of that group!

 * Starting VirtualBox kernel module vboxdrv FATAL: Module vboxdrv not found.

 * Modprobe vboxdrv failed. Please use 'dmesg' to find out why.
invoke-rc.d: initscript virtualbox, action "start" failed.
dpkg: error processing virtualbox (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 virtualbox
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

(i'm using dapper)

---

### Post by mcduck on 2007-02-23
Try running 'sudo vmware-uninstall.pl'

---

### Post by seshomaru samma on 2007-02-23
```
sesho@laptop:~$ sudo vmware-uninstall.pl
....
The removal of VMware Server 1.0.1 build-29996 for Linux completed
successfully. Thank you for having tried this software.
```


Thanks!

---

### Post by definewebsites on 2007-10-09
I tried installing vmware server, and encountered problems. It was asking me for directories where things were located and I just kept pressing enter as I wasn't sure what to do, then the installation just ended with an error.

When I tried to run it again, it said that "previous installation of vmware detected", even though the installation never completed.

Now I cannot find anyway to remove what has been done.

Any ideas..

:(

---

### Post by definewebsites on 2007-10-09
I would appreciate it...

---

### Post by Kymus on 2007-10-20
I am receiving a similar error.
[INDENT]
A previous installation of a VMware product has been detected

If you installed it from the VMware website, please remove it by running vmware-uninstall.pl before proceeding.

If it was installed through Ubuntu, you must purge (completely remove) the old package.[/INDENT]

I've tried "sudo vmware-uninstall.pl" to which I just get the error that the command was not found..:confused:

---

### Post by definewebsites on 2007-10-20
Hmm, I am getting the feeling that the only way to get the vmware out of the system is to reinstall ubuntu. Something that I really do not want to have to do due to the time and effort involved. Does anyone have any suggestions as to what can be done next.

Thanks

:(

---

### Post by Kymus on 2007-10-20
> **definewebsites said:**
> Hmm, I am getting the feeling that the only way to get the vmware out of the system is to reinstall ubuntu.

my god I hope not

---

### Post by GregOlm on 2007-10-20
I was able to get around this by doing a ```
sudo rm -Rf /etc/vmware/
``` hope this helps

---

### Post by definewebsites on 2007-10-21
Hi,

Thanks for the response. Funny enough I did try that and the system told me that I did not have permissions to do that even though I was logged in as administrator. I even altered the permissions of the folder to read/write, but I was still not permitted to remove the folder. Its like the system has locked onto the folder.

:(

---

### Post by Darkstrike on 2007-10-23
This is what I did to install Vmware Server on Ubuntu Gusty:

[http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/](http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/)

It is a great tutorial and it shows you exactly what to do.

My issue is that USB devices will not show up within the Virtual Machine, even when I try to go through VMware it doesn't detect them. And that Full Screen mode won't work because it says that it cannot detect my mouse. Otherwise XP is running great with no noticeable slow downs from when I had it running by itself. 

Hope this Helps!

---

### Post by zaphod777 on 2007-10-23
if you use virtual box it will work seamlesly with USB mouse and full screen.

---

### Post by definewebsites on 2007-10-23
Hi,

I tried using virtual box. I got it up and running, and proceeded with installing Microsoft Windows XP. However, when it got to the point of formatting the virtual partition in the initial setup, after 5 hours, it had not moved past the 0% mark.

Anyone have any idea why I could not go through the Windows XP setup?

:(

---

### Post by zaphod777 on 2007-10-23
try and use the partition in the default location not on an external drive.

---

### Post by vcinfio on 2007-10-28
hey thanks that code really helped and now its working fine

```
sudo rm -Rf /etc/vmware/
```

---

### Post by thekman on 2007-11-01
hey guys,

did some playing around uninstalling vmware.

I used:

sudo ./vmware-server-distrib/bin/vmware-uninstall.pl


don't know if you had figured this out but thought I'd post anyway.

---

### Post by pmorton on 2007-11-18
> **seshomaru samma said:**
> thanks but i'm getting this error with virtualbox:
[CODE]Creating group 'vboxusers'. VM users must be member of that group!
r)

Make yourself a member of the VirtualBox group. Go to System/Administration/Users and Groups/Manage Groups and add yourself to the 'vboxusers' group.

---

### Post by tomcat2007 on 2008-04-12
> **definewebsites said:**
> Hmm, I am getting the feeling that the only way to get the vmware out of the system is to reinstall ubuntu.I ran into the same problem and after trying to remove the installation manually, found the partition to which it had been installed will no longer boot.  

This probably stems from the fact that the vmware player in the repo will not install and I had to get a version compatible with AMD 64 bit CPUs from VMWARE.  Yes, I'm still a linux newb so it didn't occur that the .deb file wouldn't populate synaptic with uninstall info and the lesson I have learned from this experience is to ignore any product that isn't installed from a repo.  Since there are open source virtual solutions available, I'm washing my hands of VMWARE.

Ah well, live and learn ;-)

---

### Post by olskar on 2008-04-21
If anyone else get this problem:

cd /etc/vmware

then:

sudo ./installer.sh uninstall

---

### Post by joechiang on 2008-04-29
> **olskar said:**
> If anyone else get this problem:

cd /etc/vmware

then:

sudo ./installer.sh uninstall


thank you, your script is the only script works for me

vmware workstation 6.0.2

ubuntu hardy heron 32bit

---

### Post by davescar on 2008-05-02
> **thekman said:**
> hey guys,

did some playing around uninstalling vmware.

I used:

sudo ./vmware-server-distrib/bin/vmware-uninstall.pl


don't know if you had figured this out but thought I'd post anyway.

Why is it that the easiest answer is always the most elusive?  Thanks for the tip!

---

### Post by tw3k on 2008-05-02
I really _really_ hate to be a smart ***. Ok, not all the time.

Does VM stand for Vapor Machine?

---

### Post by Japhar on 2008-06-06
It might be a bit too late for the original person making the post, but here is how I unstall vmware server. When you first install the software in the mass of questions it tells you how to uninstall the server. If you didn't write it down, like most of us, you can login as su and issue the command locate vmware-uninstall.pl at the root directory to find the location. There may be two copies on your hard drive. Most likely it is in the /usr/bin directory. As root, change into the directory (e.g. cd /usr/bin) and type in the command ./vmware-install.pl

This should do the trick.

---

### Post by awahid2020 on 2008-06-17
> **mcduck said:**
> Try running 'sudo vmware-uninstall.pl'



Thanks Mate, This command really worked for me, I want to try virtualbox instead of VMware server.

thanks again mate

---

