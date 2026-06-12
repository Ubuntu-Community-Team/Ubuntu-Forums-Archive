---
title: "I have multiple kernels installed, can I remove some?"
date: 2006-07-10
forum: General Help
---

### Post by Boomy on 2006-07-10
Grub has a long list of kernels and I'd like to clean it up. I have like 5 or 6 kernels installed, can I just keep one and unistall the others?

---

### Post by simonn on 2006-07-10
yep

---

### Post by slimdog360 on 2006-07-10
I dont think you can get rid of them but you can however stop them from showing up.
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```
which creates a backup
then```
sudo gedit /boot/grub/menu.lst
```

scroll down till you see the section which looks like the bit which shows up during startup.
You can put a # in front of the thigns you dont want to show up. eg mine looks like

title		Ubuntu, kernel 2.6.15-25-386
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

#title		Ubuntu, kernel 2.6.15-23-386
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-23-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb1 ro single
#initrd		/boot/initrd.img-2.6.15-23-386
#boot

notice how I put #'s in front the the kernal I didnt want to show.

---

### Post by RAOF on 2006-07-10
Of course you can remove some of the surplus kernels.  Just search for them in Synaptic (or, from a terminal, aptitude search) and select them for removal.  You can remove whichever kernels you like, but make sure not to remove the latest one.  Or, alternatively, make sure you have a linux-*something* (like linux-386, linux-k7, etc) metapackage installed - that way you'll **definitely** have a kernel at the end :)  

It will warn you if you're removing the kernel that you're currently running, though :)

---

### Post by Boomy on 2006-07-10
thanks for the info. :)

---

### Post by humdinger70 on 2006-07-10
Just a note about updating the GRUB list...

The easier way is to limit the list by modifying the #howmany line in the /boot/grub/menu.lst file. By default, it will display ALL of them. I set mine to 4 (change it to read #howmany=4 - be sure to keep it as a comment!) then run sudo update-grub.

Note: it will keep (in my case) 4 copies of UNIQUE versions of the kernel; the recovery ones don't count as unique!

Also, you may want to go into /boot and delete the older versions of the files (System.map, vmlinuz, initrd, etc.) for kernel versions you don't want to keep around. They can take up several megabytes of space, which could be a problem if you're tight on disk space, or you have /boot as a separate partition and haven't allocated a lot of space to it.

---

### Post by RAOF on 2006-07-10
> **humdinger70 said:**
> ...
Also, you may want to go into /boot and delete the older versions of the files (System.map, vmlinuz, initrd, etc.) for kernel versions you don't want to keep around. They can take up several megabytes of space, which could be a problem if you're tight on disk space, or you have /boot as a separate partition and haven't allocated a lot of space to it.
Just remove the linux-image-2.6.15-*foo* packages!  That will remove all of those files, **plus** the 90MB or so of kernel modules.  Safely.

As a general rule, if you're trying to do something manually to files outside of your home folder, there's an easier way to do it.  In this case, the package manager - Synaptic/apt-get/aptitude, whichever front-end you prefer.  These manual "edit this file", "delete these files" solutions are just more difficult (and less complete) than using the package manager; that's what it's **designed** for :).

---

### Post by mduran on 2006-07-10
with :

```

dpkg --purge --force-remove-essential linux-image-NNN

```


according to debian reference :
[http://www.debian.org/doc/manuals/reference/ch-system.en.html#s-removeoldkernel](http://www.debian.org/doc/manuals/reference/ch-system.en.html#s-removeoldkernel)

---

### Post by RAOF on 2006-07-10
> **mduran said:**
> with :

```

dpkg --purge --force-remove-essential linux-image-NNN

```

according to debian reference :
[http://www.debian.org/doc/manuals/reference/ch-system.en.html#s-removeoldkernel](http://www.debian.org/doc/manuals/reference/ch-system.en.html#s-removeoldkernel)
You could do that, but it it's unnecessarily difficult, and might leave packages which depend on the linux-image behind (packages like **linux-restricted-modules-*version*** for example).  There's been a lot of not quite right, or unnecessarily difficult stuff presented in this thread.  How about I provide a summary of (what I think is) the **easiest** ways to do this:

**With a GUI**
1) Go to Synaptic package manager (System->Administration->Synaptic Package Manager).  Enter your password when it asks.
2) Hit the "search" button.  Search for "linux-image" (in package name only, if you want to be more specific)
3) The results will be all the kernels Synaptic knows about.  The ones marked with a green square are the ones you have installed.  
4) Right click on each of the installed ones you want to remove, and select "remove"
5) Once you've selected all the ones you want to remove, hit the "Apply" button.

Done.

**From the command-line**
```
sudo aptitude remove linux-image-*version_number*
```
Where *version_number* is the version number of the kernel you want to remove.  
You can check what kernels you have installed with
```
aptitude search linux-image
```
This will list all the kernels the package manager knows about.  An "i" at the start of the line indicates that the kernel is installed.

Both of these approaches will work, and are guaranteed to not break your system (or rather, will say "You're trying to remove the running kernel.  You probably don't want to do this.  Are you **sure** you want to do this?" first :)).  Also, they'll leave your system clean - no files relating to the kernel that you removed will be left lying around.

---

### Post by Anduu on 2006-07-10
> **RAOF said:**
> As a general rule, if you're trying to do something manually to files outside of your home folder, there's an easier way to do it.  In this case, the package manager - Synaptic/apt-get/aptitude, whichever front-end you prefer.  These manual "edit this file", "delete these files" solutions are just more difficult (and less complete) than using the package manager; that's what it's **designed** for :).

[B][I]
AMEN![/I][/B]

Just because this is Linux some people think using a GUI is lame...I don't get it...

---

### Post by usererror on 2006-07-11
great post, thank you! :D

---

### Post by prabhakar2 on 2006-07-11
> **RAOF said:**
> You could do that, but it it's unnecessarily difficult, and might leave packages which depend on the linux-image behind (packages like **linux-restricted-modules-*version*** for example).  There's been a lot of not quite right, or unnecessarily difficult stuff presented in this thread.  How about I provide a summary of (what I think is) the **easiest** ways to do this:

**With a GUI**
1) Go to Synaptic package manager (System->Administration->Synaptic Package Manager).  Enter your password when it asks.
2) Hit the "search" button.  Search for "linux-image" (in package name only, if you want to be more specific)
3) The results will be all the kernels Synaptic knows about.  The ones marked with a green square are the ones you have installed.  
4) Right click on each of the installed ones you want to remove, and select "remove"
5) Once you've selected all the ones you want to remove, hit the "Apply" button.

Done.

**From the command-line**
```
sudo aptitude remove linux-image-*version_number*
```
Where *version_number* is the version number of the kernel you want to remove.  
You can check what kernels you have installed with
```
aptitude search linux-image
```
This will list all the kernels the package manager knows about.  An "i" at the start of the line indicates that the kernel is installed.

Both of these approaches will work, and are guaranteed to not break your system (or rather, will say "You're trying to remove the running kernel.  You probably don't want to do this.  Are you **sure** you want to do this?" first :)).  Also, they'll leave your system clean - no files relating to the kernel that you removed will be left lying around.



great information
thanks

---

### Post by mduran on 2006-07-11
yep,
in ubuntu exist "linux-restricted".

---

