---
title: "[SOLVED] After cleaning kernels a weird error occurs"
date: 2008-06-25
forum: General Help
---

### Post by hokiesparkles on 2008-06-25
After cleaning up the kernels that were available on my boot screen, I tried to add/remove programs but I received this message:

"Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'."

After I did 'sudo apt-get update' everything went ok, no errors or anything. But when I did 'sudo apt-get install -f', this is what proceeds:

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-ubuntu-modules-2.6.22-14-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 9843kB disk space will be freed.
Do you want to continue [Y/n]? " (I put Y & enter)

"(Reading database ... 110705 files and directories currently installed.)
Removing linux-ubuntu-modules-2.6.22-14-generic ...
FATAL: Could not open '/boot/System.map-2.6.22-14-generic': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
Cannot find /lib/modules/2.6.22-14-generic
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
dpkg: error processing linux-ubuntu-modules-2.6.22-14-generic (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-ubuntu-modules-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)"

I'm not sure what I'm supposed to do after this. :(
I'm really new with Ubuntu (I'm using Hardy).
Can someone please help me fix this problem?

Thanks!

---

### Post by drs305 on 2008-06-25
If you want the latest kernel, go to synaptic, and try to reinstall 'linux-image'. It's a metapackage which should install the latest kernel and dependencies. You can also look at the left side tabs and see if there are broken packages.

If you get errors about kernel 14 please let us know which kernel you are currently using: 
```
uname -r
```

---

### Post by hokiesparkles on 2008-06-25
I went to synaptic and try to re-install 'linux-image' but I got the same error of:
'E: linux-ubuntu-modules-2.6.22-14-generic: subprocess post-removal script returned error exit status 1'

I do have broken dependencies, it's this: 'linux-ubuntu-modules-2.6.22-14-generic
Ubuntu supplied Linux modules for version 2.6.22 on x86/x86_64'

The kernel I'm using is 2.6.24-19-generic.

---

### Post by drs305 on 2008-06-25
> **hokiesparkles said:**
> I went to synaptic and try to re-install 'linux-image' but I got the same error of:
'E: linux-ubuntu-modules-2.6.22-14-generic: subprocess post-removal script returned error exit status 1'

The kernel I'm using is 2.6.24-19-generic.

The error-causing kernel is pretty old and can safely be removed (and reinstalled later should you need it). To get rid of the error(s):
```

sudo rm /var/lib/dpkg/info/linux-ubuntu-modules-2.6.22-14*

```

Then run:
```

sudo apt-get update
sudo apt-get upgrade
```

---

### Post by hokiesparkles on 2008-06-25
I did all that and everything works great. No error messages when I try to add/remove or when I run Synaptic package manager.

Thanks so much for helping me out! I really appreciate it. :)

---

### Post by drs305 on 2008-06-25
Glad it worked for you. 

If you really want to tempt fate, there are probably residual files around because of the way we dealt with this. You could go into synaptic, install kernel 14 (if it's available to you) and then mark for  complete removal. ...  Okay, so maybe you won't.

Anyway, if you consider this solved please use the Thread Tools to mark it so.

---

### Post by Endolith on 2008-12-08
> **drs305 said:**
> Glad it worked for you. 

If you really want to tempt fate, there are probably residual files around because of the way we dealt with this. You could go into synaptic, install kernel 14 (if it's available to you) and then mark for  complete removal. ...  Okay, so maybe you won't.

Anyway, if you consider this solved please use the Thread Tools to mark it so.

Do you know what the other files are?  I am getting the same error when I try to remove linux-ubuntu-modules-2.6.22-14-generic, but it doesn't list anything in "Installed files", and I can't re-install and then re-remove, either:

> linux-ubuntu-modules-2.6.22-14-generic:

Package linux-ubuntu-modules-2.6.22-14-generic has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list



---

### Post by Endolith on 2008-12-08
Actually:

```
~> locate "/*2.6.22*"
/var/lib/dpkg/info/linux-ubuntu-modules-2.6.22-14-generic.list
/var/lib/dpkg/info/linux-ubuntu-modules-2.6.22-14-generic.postrm

```So I don't have to worry about it, right?  Just remove both of those files?  There's no huge kernel image floating around anywhere?

---

### Post by drs305 on 2008-12-08
I was just writing a response when I saw your latest post. I was going to use the find command (sudo find / -iname "*2.6.22-14*" ) but your solution should work as well. 

The error message is not saying there are 22-14 files still on your system (which is what the commands above do - find files) - just that the old kernel is still mentioned somewhere in the dpkg database. Even if you can't get rid of this message you shouldn't lose sleep over it. ;-)

---

