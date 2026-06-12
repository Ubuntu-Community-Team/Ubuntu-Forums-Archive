---
title: "Software Index is Broken!"
date: 2007-02-08
forum: General Help
---

### Post by bg1256 on 2007-02-08
First off, I'm running Edgy / Gnome.

This morning I received the following message when attempting to update through update manager:

> Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

When I run sudo apt-get install -f, I get the following output: 
```
benjamin@BG-Desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-image-generic linux-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  linux-generic linux-image-generic
0 upgraded, 0 newly installed, 2 to remove and 2 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 106kB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

I'm nervous to remove this, because I'm using the generic kernel, and I don't want to completely bork my system.  Does this just mean the generic kernel has been updated?

The only thing I can think of that would have caused this is yesterday I installed kubuntu-desktop through apt-get, just to see what KDE was like.  I followed a guide here on the forums, and everything seemed  to be fine both in KDE and Gnome yesterday.  Today seems to be a different story.

Any ideas for what to do here?

---

### Post by etank on 2007-02-08
Try using aptitude instead of apt-get.```
sudo aptitude -f install
```

---

### Post by teaker1s on 2007-02-08
look at this thread,I had similar issue and this is how to fix it
[http://www.ubuntuforums.org/showthread.php?t=187765](http://www.ubuntuforums.org/showthread.php?t=187765)

---

### Post by bg1256 on 2007-02-08
> **etank said:**
> Try using aptitude instead of apt-get.```
sudo aptitude -f install
```

Output is:

```
benjamin@BG-Desktop:~$ sudo aptitude -f install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages are BROKEN:
  linux-image-generic 
The following packages have been automatically kept back:
  linux-restricted-modules-generic 
The following packages have been kept back:
  linux-headers-generic 
0 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  linux-image-generic: Depends: linux-image-2.6.17-11-generic which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Downgrade the following packages:
linux-image-generic [2.6.17.11 (edgy-security, edgy-security, now) -> 2.6.17.10
(edgy)]

Score is -40

Accept this solution? [Y/n/q/?] 

```

Should I accept?

I have not accepted yet, because I'm not sure what it will do.


> look at this thread,I had similar issue and this is how to fix it

I actually read this thread before I posted.  I see that it is a similar issue; however, I'm unable to run apt-get install right now.  I tried sudo apt-get remove kubuntu-desktop as well as install ubuntu-desktop, and I get error messages.

---

### Post by bg1256 on 2007-02-10
Just a bump here.

I'm hoping someone can let me know if it's safe to go through with 
```
sudo aptitude -f install
```

---

### Post by bg1256 on 2007-02-11
Solved.

 I had to manually install the kernel update to linux-image-2.6.17-11-generic

---

