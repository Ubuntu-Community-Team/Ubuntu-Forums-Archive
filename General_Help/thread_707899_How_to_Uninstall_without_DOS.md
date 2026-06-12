---
title: "How to Uninstall without DOS"
date: 2008-02-25
forum: General Help
---

### Post by chile13 on 2008-02-25
I install Linux with full partition and now I have to uninstall and partition differently.  I cannot find any posts anywhere on how to uninstall Linux without a DOS command prompt.   I am working with a client using an Enterprise software and it's not compatable. Therefore I must install XP to access the Enterprise.  When I tried to install XP of course there is not drive available.  HELP!!!

---

### Post by HermanAB on 2008-02-25
Boot with a live CD (Knoppix?) and run Partimage.  Then reformat the whole disk as VFAT.

After that, Windows will install again.

---

### Post by chile13 on 2008-02-25
I'm new to Ubuntu so I have ask.  What is Knoppix?

---

### Post by torgrot on 2008-02-25
Just use the CD you used to install Ubuntu.  Select Applications -> Accessories-> PartImage or something similiar, I don't remember.  It may be Qparted.

torgrot

---

### Post by y-lee on 2008-02-25
> I'm new to Ubuntu so I have ask. What is Knoppix?

[Knoppix]("http://php.8ez.com/drsmall/blog/?p=178") is a linux live cd and it can be used as an operating system of its own much like ubuntu.

See also [Knoppix]("http://www.knoppix.net/") web site to download

EDIT: torgrot is right the ubuntu live cd can be used for partitioning also.

---

### Post by chile13 on 2008-02-25
There is nothing in Application-Accessories-etc. even remotely close to your instructions.
Is this on the CD or installed somewhere?

---

### Post by chile13 on 2008-02-25
Can I use the Terminal command area to do this?

---

### Post by chile13 on 2008-02-25
I'm using 7.10 i386 on my CD???

---

### Post by y-lee on 2008-02-25
Boot up a live CD and in your live session, install GParted.

```
sudo aptitude update && sudo aptitude install gparted
```

---

### Post by louieb on 2008-02-25
Its System>Adminstration>Partition Editor
or my favorite get yourself a [SystemRescueCd]("http://www.sysresccd.org/Main_Page") its a great software toolset for anyone working on PCs.

---

### Post by y-lee on 2008-02-25
> I cannot find any posts anywhere on how to uninstall Linux without a DOS command prompt. I am working with a client using an Enterprise software and it's not compatable. Therefore I must install XP to access the Enterprise

Really tho you should be able to  pop the XP cd in, and when it boots into the XP  install, delete all the partitions (or keep some if you want) and go through the rest of the XP install. that would be easier.

---

### Post by chile13 on 2008-02-25
Ok, now I'm really confused.  I do not have the Partition Editor under System-Administration either!!! 

Is the live CD different than the installation CD?

You guys are great an i really appreciate your help

---

### Post by y-lee on 2008-02-25
> Ok, now I'm really confused. I do not have the Partition Editor under System-Administration either!!!

Is the live CD different than the installation CD?

You guys are great an i really appreciate your help

the Live CD is the installation Cd.

The partition editor must be installed, it is called GParted and can be found in synaptic or installed by the command I gave above. You must use the Live CD if you are wiping Ubuntu out.

the XP CD should allow you to delete partitions tho. And I gotta go so I hope ya work it out. :)

---

### Post by y-lee on 2008-02-25
If you do use gparted  be aware windows XP uses a NTFS partition :)

---

### Post by eriqjaffe on 2008-02-25
Why not just run Windows in VMWare or VirtualBox?

---

### Post by louieb on 2008-02-26
> **chile13 said:**
> Ok, now I'm really confused.  I do not have the Partition Editor under System-Administration either!!! 

I'm wondering now what Linux Live CD you have. Put it in a working computer and see what the title is. The older Ubuntu versions call GParted something else cant remember just what. 

Which XP disk do you have (full or upgrade)? If I remember right the upgrade CD won't format a hard drive. 
>  			 				I'm new to Ubuntu so I have ask. What is Knoppix?

Its another Linux distribution.  One of the best for rescue and repair work. [DistroWatch.com: Put the fun back into computing. Use Linux, BSD.]("http://distrowatch.com/")
Good Luck.

---

