---
title: "I Need Access To A FIle Written On A Windows Machine"
date: 2006-11-08
forum: General Help
---

### Post by Mark76 on 2006-11-08
Can I do it? :-k

---

### Post by IronArjen on 2006-11-08
Can you give more specifics? Is your machine in a net? Do you have the file on a portable medium (CD or stick)? Stuff like that and more............

---

### Post by Mark76 on 2006-11-08
It's on a floppy disc.  It's a CV I made on another computer using Word 2003.

No my machine isn't in a net.

---

### Post by glotz on 2006-11-08
Sure you can. I don't understand where the problem lies.

---

### Post by Peepsalot on 2006-11-08
> **Mark76 said:**
> It's on a floppy disc.  It's a CV I made on another computer using Word 2003.

No my machine isn't in a net.

You should be able to just pop the disk in and read it.  Linux support FAT file systems, which is what(i'm pretty sure) a floppy would normally be formatted to.

I don't have a floppy drive, but I believe that Ubuntu will put a new icon on the desktop for it when you put it(or other removable media) in.

---

### Post by itismike on 2006-11-08
> **Peepsalot said:**
> You should be able to just pop the disk in and read it.  
[...]I believe that Ubuntu will put a new icon on the desktop for it when you put it(or other removable media) in.

You're exactly right, Peepsalot - Ubuntu SHOULD be able to simply offer immediate access to a floppy.  It does offer immediate access to USB and optical media, but because floppy's don't cause a detectable system event when they are inserted, there is no way to start the service.

Since my PC has a floppy drive installed, I would expect to find 'Floppy' under the 'Places' drop-down menu on the Ubuntu launch panel.  Nada. ](*,) 

I would also expect to find a useful function under Disks in the System > Administration menu.  While it does provide an icon for Floppy, it does nothing but look enticing. ](*,) 

Surely I am missing something.  I know how to mount a floppy from the command line (or could figure it out in a few minutes on Google), but why is this not more obvious to me? :-k 


To the original poster:

The easiest method to get this file to your Ubuntu box is likely to email it to yourself or put it on a flash/thumb drive.  Alternatively, you could do what I'm about to do and perform a Google search for the solution using keywords: Linux, mount, floppy, windows.  Here is one well-written solution:
[http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)
*** keep in mind that the above guide neglects to use 'sudo' in front of certain commands.  You'll have to add that to their examples when you get "Access Denied"-type messages.  See this forum for more details on using sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Peepsalot on 2006-11-08
> **itismike said:**
> You're exactly right, Peepsalot - Ubuntu SHOULD be able to simply offer immediate access to a floppy.  It does offer immediate access to USB and optical media, but because floppy's don't cause a detectable system event when they are inserted, there is no way to start the service.

Since my PC has a floppy drive installed, I would expect to find 'Floppy' under the 'Places' drop-down menu on the Ubuntu launch panel.  Nada. ](*,) 

I would also expect to find a useful function under Disks in the System > Administration menu.  While it does provide an icon for Floppy, it does nothing but look enticing. ](*,) 

Well that's a bummer.  I did a search for "automount floppy" on these forums and found this: [http://ubuntuforums.org/showthread.php?t=195298&highlight=automount+floppy](http://ubuntuforums.org/showthread.php?t=195298&highlight=automount+floppy)
Hopefully that will help.

Good luck, and let us know how things work out.

Maybe someone can convince those in charge to put submount in the repositories.  That is, of course, assuming it works for you all.

---

### Post by Mark76 on 2006-11-09
> Submount subfs installation intructions.

To compile and install the module, the kernel with which you will use the
module should be running.  The makefile expects to find the kernel source
directory linked to /lib/modules/<kernel-version>/build, as it should
have been by the "make modules_install" command.  The cuurent version should
work with kernel versions starting with 2.6.0-test1.

Type "make" in this directory, and then, as root, type "make install".  The
module is named subfs.ko, and is installed in the
/lib/modules/<kernel-version>/kernel/fs/subfs directory.  "modprobe subfs"
should load the module.

For usage instructions, see the README file in the top level directory of the
submount package.mazke


I wish I knew which kernel it was talking about :(

---

### Post by Peepsalot on 2006-11-09
I think it would be whichever version is chosen form your grub boot menu.
Try this in terminal
```
uname -a
```
On mine the third column represents the current kernel version.

Edit: actually i think "uname -r" is the more precise answer.

---

### Post by Mark76 on 2006-11-09
Okay, I now know which kernel it is.  But what does it mean by "should be running"?

---

### Post by Peepsalot on 2006-11-09
> **Mark76 said:**
> Okay, I now know which kernel it is.  But what does it mean by "should be running"?
It basically means you need to have booted normally before you do this.

When you boot up, depending on your setup, you may have more than one option for kernel versions in your grub boot menu.  You should choose the one that you want to install this for(presumably the one you normally boot everytime).  

If you boot from a LiveCD for example, then you will be running the kernel that is on the CDm which is different from the one on your hard drive.  If you try to install it in this way, it probably won't work.  Also, in this case, if you run "uname -r", it tells you the kernel version that is currently running.  So it would tell you the kernel version on the CD, not the one from your hard drive.

---

### Post by Mark76 on 2006-11-15
I keep having a hard time with the Make command

mark-williams@cpc1-nfds11-0-0-cust975williams:~$ cd /lib/modules/2.6.15-27-386
mark-williams@cpc1-nfds11-0-0-cust975williams:/lib/modules/2.6.15-27-386$ make
make: *** No targets specified and no makefile found. Stop.
mark-williams@cpc1-nfds11-0-0-cust975williams:/lib/modules/2.6.15-27-386$ sudo make install subfs.ko
Password:
make: *** No rule to make target `install'. Stop.
mark-williams@cpc1-nfds11-0-0-cust975williams:/lib/modules/2.6.15-27-386$

---

