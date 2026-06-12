---
title: "Run Windows Partition with a SATA Hard drive"
date: 2008-02-21
forum: General Help
---

### Post by DizzyThermal on 2008-02-21
Hey guys, first of all I'd like to say thank you to everyone who's helped me on my previous posts and am happy to say I did get VMware working with my other partition.  Just one problem, that drive was junk!  It failed 3 times within a month with a DISK BOOT FAILURE Error.  So I got a new 250GB HDD that is Serial ATA (SATA)

I have been reading the same tutorial to get it working that last time, but it is a tutorial for a regular ide hard drive.

I noticed this once I used GParted to try to find out hard drive information for /dev/hda

I couldn't find it, so I did **fdisk -l** and saw it was all /dev/sda1   /dev/sda2 and so on.

So as I was reading the vmx file and vmdk file I saw things like, [ddb.adapterType = "ide"] and [ide0:0.fileName = "WindowsXP.vmdk"] and was like, crap, I don't know how to port this to make it work for SATA...

I did a little research and heard about scsi, but couldn't find a tutorial to help with it and was wondering if anyone has ran into this issue or would know how to help.  The tutorial is located here:  [http://oopsilon.com/Running-a-Windows-Partition-in-VMware](http://oopsilon.com/Running-a-Windows-Partition-in-VMware)

I have done everything correctly but I just need to know how to replace the ide things in the VMX and VMDK files.  I know it doesn't work because if I double click the VMX file I get this error:```
Error opening virtual machine /home/dizzy/VMware/WindowsXP.vmx: File "/home/dizzy/VMware/WindowsXP.vmx" line 42: Syntax error.
```

Hey, thanks guys for the help in advance and I hope I can get some help here :)!

---

### Post by pointone on 2008-02-22
SATA drives are not SCSI. SATA/PATA is "equivalent" to to IDE. See [this]("http://en.wikipedia.org/wiki/AT_Attachment") for more information.

At some point, the Linux kernel just changed the naming scheme from hd* to sd*; that's all. Everything else in the guide should still be valid.

---

### Post by DizzyThermal on 2008-02-22
Then what do you think the error I posted is for?  Before, with this set up it would work fine in VMware.  Hmmm... :(

---

### Post by DizzyThermal on 2008-02-22
Okay, I went to line 42 and made sure there were no spaces before or after and resaved it.  It works now... But I get this error:  Can't find WindowsXP.vmdk...  I had this error before in a previous post and here was my fix:

**Solved!**
====================================
**Unmounted the windows partition:**

```
sudo su
umount -a
```

**Changed the permissions on the mount:**

```
sudo su
cd /media
chown dizzy windows
```

***Note*: Keep the partition _unmounted_***

This worked for me guys :)
====================================

But it doesn't work this time...  Not sure how to fix it... :(

---

### Post by pointone on 2008-02-22
Well, it's complaining about line 42... Why not post the line here?

---

### Post by DizzyThermal on 2008-02-22
> **DizzyThermal said:**
> Okay, I went to line 42 and made sure there were no spaces before or after and resaved it.  It works now...

Sorry if that seemed like I said it with attitude, it wasn't meant to.

But, now I'm having the other error I stated above.

---

### Post by DizzyThermal on 2008-02-22
Alrighty, almost there!

I use the *sudo nautilus* command and I browse to /home/dizzy/VMware and I double click WindowsXP.vmx and it works!  There is something about me running it as dizzy that isn't letting me do it.  Anyone know how I can make it so I can just run it without having to use *sudo nautilus* all the time?  Thanks :)

---

### Post by pointone on 2008-02-23
Sorry; I think I misread your post. I thought you were still having the same problem.

What are the permissions on the file? Try owning it/granting full read/write and see if that solves the problem (assuming it's not already set this way).

---

### Post by DizzyThermal on 2008-02-23
I have already done **chown dizzy VMware** and **chmod 777 *.***

Not sure what else I can do... :(

---

### Post by DizzyThermal on 2008-02-24
Anyone know why even after changing the owner to my username and running chmod 777 *.* I still have to use sudo nautlius in order to run WindowsXP.vmx?

Thanks in advance :)

---

