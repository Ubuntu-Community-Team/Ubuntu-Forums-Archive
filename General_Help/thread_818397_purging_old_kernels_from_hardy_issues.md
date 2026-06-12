---
title: "purging old kernels from hardy issues"
date: 2008-06-04
forum: General Help
---

### Post by trmentry on 2008-06-04
I'm having a bit of an odd issue.  I logged on today and saw that there was an updated kernel.  2.6.24-18.  

I went to install it and it error out.  After digging turns out my /boot was full.

So I went to Synaptic and told it to purge -16 kernel.  After that, -18 installed fine.  After I got -18 running and vmware wkst recompiled.  I went back to Synaptic and told it to purge -17.  

Now I'm getting this.

```

E: linux-backports-modules-2.6.24-16-generic: subprocess post-removal script returned error exit status 1
E: linux-backports-modules-2.6.24-17-generic: subprocess post-removal script returned error exit status 1
E: linux-ubuntu-modules-2.6.24-16-generic: subprocess post-removal script returned error exit status 1
E: linux-ubuntu-modules-2.6.24-17-generic: subprocess post-removal script returned error exit status 1

```

```

(Reading database ... 113971 files and directories currently installed.)
Removing linux-backports-modules-2.6.24-16-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-16-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Cannot find /lib/modules/2.6.24-16-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: error processing linux-backports-modules-2.6.24-16-generic (--remove):
 subprocess post-removal script returned error exit status 1
Removing linux-backports-modules-2.6.24-17-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-17-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic
Cannot find /lib/modules/2.6.24-17-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: error processing linux-backports-modules-2.6.24-17-generic (--remove):
 subprocess post-removal script returned error exit status 1
Removing linux-ubuntu-modules-2.6.24-16-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-16-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Cannot find /lib/modules/2.6.24-16-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-16-generic (--remove):
 subprocess post-removal script returned error exit status 1
Removing linux-ubuntu-modules-2.6.24-17-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-17-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic
Cannot find /lib/modules/2.6.24-17-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-17-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-backports-modules-2.6.24-16-generic
 linux-backports-modules-2.6.24-17-generic
 linux-ubuntu-modules-2.6.24-16-generic
 linux-ubuntu-modules-2.6.24-17-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:



```

I'm trying to figure out why its wanting to erase files it already erased and then is causing issues.

Can some one please help me out?

Thanks

NOTE: My /boot partition is 50M.

---

### Post by trmentry on 2008-06-04
Ok.. this is having interesting side effects on my system.  I can't install anything.

I was trying to install something and it says...

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-backports-modules-2.6.24-16-generic
  linux-backports-modules-2.6.24-17-generic
  linux-ubuntu-modules-2.6.24-16-generic
  linux-ubuntu-modules-2.6.24-17-generic
The following NEW packages will be installed:
  google-desktop-linux picasa
0 upgraded, 2 newly installed, 4 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 32.3MB of archives.
After this operation, 77.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://dl.google.com stable/non-free google-desktop-linux 1.2.0.0088 [8236kB]
Get:2 http://dl.google.com stable/non-free picasa 2.7.3736-15 [24.1MB]
Fetched 32.3MB in 4min9s (130kB/s)
(Reading database ... 113971 files and directories currently installed.)

```

After that.. it attempts to remove the linux stuff and fails... and doesn't install the apps above.

I tried to go into synaptic to unmark the removals, but that didn't help as it then wanted to INSTALL the older versions again... and since I don't have space.. that wouldn't work.

---

### Post by buntunub on 2008-06-04
Try,

```
$sudo apt-get autoremove
```

See if that helps purge the old kernels and fix that residual issue.

---

### Post by trmentry on 2008-06-04
No joy. :(

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED:
  linux-backports-modules-2.6.24-16-generic
  linux-backports-modules-2.6.24-17-generic
  linux-ubuntu-modules-2.6.24-16-generic
  linux-ubuntu-modules-2.6.24-17-generic
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 33.7MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 113971 files and directories currently installed.)
Removing linux-backports-modules-2.6.24-16-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-16-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Cannot find /lib/modules/2.6.24-16-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: error processing linux-backports-modules-2.6.24-16-generic (--remove):
 subprocess post-removal script returned error exit status 1
Removing linux-backports-modules-2.6.24-17-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-17-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic
Cannot find /lib/modules/2.6.24-17-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: error processing linux-backports-modules-2.6.24-17-generic (--remove):
 subprocess post-removal script returned error exit status 1
Removing linux-ubuntu-modules-2.6.24-16-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-16-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Cannot find /lib/modules/2.6.24-16-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-16-generic (--remove):
 subprocess post-removal script returned error exit status 1
Removing linux-ubuntu-modules-2.6.24-17-generic ...
FATAL: Could not open '/boot/System.map-2.6.24-17-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic
Cannot find /lib/modules/2.6.24-17-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-17-generic
dpkg: error processing linux-ubuntu-modules-2.6.24-17-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-backports-modules-2.6.24-16-generic
 linux-backports-modules-2.6.24-17-generic
 linux-ubuntu-modules-2.6.24-16-generic
 linux-ubuntu-modules-2.6.24-17-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by fragos on 2008-06-04
I've found that easiest way for me is to open Synaptic, search for "2.6.24" and mark the packages I no longer want for removal. It updates grub for you as well.

---

### Post by trmentry on 2008-06-04
> **fragos said:**
> I've found that easiest way for me is to open Synaptic, search for "2.6.24" and mark the packages I no longer want for removal. It updates grub for you as well.

That's what got me in this trouble.   I did that, it removed the files in /boot and mod'ed Grub for me... but it didn't quite do the whole job and now can't get it to think this, it's still trying to remove the files that are gone so its fatal erroring out and completely not letting me install anything else till it gets this done.

---

### Post by fragos on 2008-06-04
This has always worked for me since Dapper.

---

### Post by buntunub on 2008-06-05
> **fragos said:**
> I've found that easiest way for me is to open Synaptic, search for "2.6.24" and mark the packages I no longer want for removal. It updates grub for you as well.

Ya, I did that last night with two of the older kernels and it worked like a champ. There is another thread about this here and that seems to be the common solution thats working for everyone. My guess is that there is something you did wrong during that process that hosed down your system good. Not sure if that is recoverable or not, but a clean reinstall might be in order.

---

### Post by cprise on 2008-06-06
I had the same problem, and resolved it by re-installing the linux-ubuntu-modules-2.6.24-16-generic package before purging both that package and the linux-ubuntu-image-2.6.24-16-generic package.

---

### Post by trmentry on 2008-06-06
> **cprise said:**
> I had the same problem, and resolved it by re-installing the linux-ubuntu-modules-2.6.24-16-generic package before purging both that package and the linux-ubuntu-image-2.6.24-16-generic package.

I went to try that as well... but my /boot said not enough space which I ws finding odd since I had -16 and -17 on there before happy.  All I had was -18 at the time but -16 wouldn't reinstall.

I had to have done something but I just can't remember what it was in the order I did to repeat this.  I've been toying with a VM to try but no luck.


Anyway......

Marius from the mail list sent me this.

> 
You can work around this problem by removing the postrm scripts that
fail and prevent apt from removing these packags.  If you're really not
going to use 2.6.24-16 and 2.6.24-17 kernels on this system (without
completely reinstalling them), that should be safe to do:

 sudo rm /var/lib/dpkg/info/linux-backports-modules-2.6.24-16-generic.postrm
 sudo rm /var/lib/dpkg/info/linux-backports-modules-2.6.24-17-generic.postrm
 sudo rm /var/lib/dpkg/info/linux-ubuntu-modules-2.6.24-16-generic.postrm
 sudo rm /var/lib/dpkg/info/linux-ubuntu-modules-2.6.24-17-generic.postrm
 sudo apt-get remove linux-ubuntu-modules-2.6.24-16-generic \
                     linux-ubuntu-modules-2.6.24-17-generic \
                     linux-backports-modules-2.6.24-16-generic \
                     linux-backports-modules-2.6.24-17-generic


And that worked.  I removed (renamed in my case) the files and then did the apt-get remove and worked like a champ.

I was then able to to a sys update for the packages that were wwanting to be installed but couldn't till this was solved.

---

