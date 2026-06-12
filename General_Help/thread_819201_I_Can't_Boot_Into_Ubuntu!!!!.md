---
title: "I Can't Boot Into Ubuntu!!!!"
date: 2008-06-05
forum: General Help
---

### Post by shuffer on 2008-06-05
I am an Ubuntu yearling and have had no trouble with my installation since I installed it. I decided to try Mandriva 2008, so overwrote my Vista installation (I have 2 hard drives in my machine, and felt I did not have to partition). I clicked on the option to overwrite all the partitions on the Vista disk and installed Mandriva on it. Now, when I open the GRUB loader, one of two things happens:

If I mark the ex-Vista now-Mandriva disk as the primary boot disk, it gives me two options: Mandriva and Longhorn. Mandriva works, but the Longhorn cannot be found.

If I use the Ubuntu hard drive as the primary boot disk, it gives me all the old options (including Ubuntu, Ubuntu Safe mode (x3) and Longhorn), but cannot find ANY of the files!!

Please help. I've been using Ubuntu for about a year and really like it, so I don't want to have to reinstall and lose all my hard-earned settings. If I reinstall, I don't know if the GRUB loader will see the Mandriva installation (which I also like) in any case.

Is there some way to 'update' the GRUB loader to see all my installations and delete the now-defunct Vista installation? I think my trouble has been caused by my having two installations of GRUB on one machine. Thanks in advance.

---

### Post by Xiong Chiamiov on 2008-06-05
You can use [SuperGrubDisk]("http://supergrubdisk.org") to solve all your GRUB problems, though it may take a little fiddling around to figure out the navigation.  Make sure to choose the option that says "(with help)" when you boot it.

---

### Post by Tom--d on 2008-06-05
Are you positive you didn't delete the Ubuntu partition and not the Vista one?

---

### Post by rraj.be on 2008-06-05
My best idea would be reinstalation of GRUB should work.

To reinstall grub

```
Boot into live cd
```

open terminal

Type

 ```
sudo grub

find /boot/grub/stage1
```

If it returned like 

hd(x,y)

enter 
 
```

root (x,y)

setup (x)

quit

sudo reboot
```

Do it with problamatic drive.

---

### Post by shuffer on 2008-06-12
Thanks for the replies guys. 

I'm pretty sure that I didn't intall Mandriva over the Ubuntu installation. I am assuming that all the partitions for Ubuntu would be on one hard drive and would not seep over some vital system elements onto the other hd. Besides, the Vista entry on the GRUB loader doesn't work either.

One thing that worries me slightly is that I cannot see any of my files when I search through the hard drive that Ubuntu is installed on from the Mandriva install. Should I be able to see Ood's and whatnot?

rraj, thanks for the tip. I am a little backward when it comes to command-line operation, so bear with me.

I have booted into Ubuntu live cd (does it have to be the same version as the install?) and tried to follow your instructions, but only get as far as accessing the GRUB command line. Do I run the routine on the hard drive with Mandriva on it, or the one with Ubuntu?

Again, thanks for the response.

---

### Post by shuffer on 2008-06-12
Update: when I try to run the setup routine (from rraj) I get 'Error 17 Cannot mount selected partition', whichever drive I run it on.

Can I run it on both drives at he same time?

When I try to run these routines direct from the command line option on the GRUB loader itself, I get the error 17 on hd1 (Ubuntu) and Error 23 'Error while parsing number' on hd0 (Mandriva disk).

---

### Post by rraj.be on 2008-06-12
just try root (hd0,0)  if you are getting like 

(hd0,0) for find/grub/stage1.

Similarly use this insteed of setup

setup(hd0)

this should work.

---

