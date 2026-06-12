---
title: "rename disk in computer:///"
date: 2007-12-16
forum: General Help
---

### Post by dachinster on 2007-12-16
Hi,
I added a new internal SATA hard drive and got it to mount, and I can read and write to it just fine. It is using ext3 filesystem.
It is also properly labelled in the "Places" menu (both the drop down and in the nautilus window) as "Backup"

However, when I go into Places>Computer it shows up as: 298.1 GB Volume: Backup

When I try to rename it, it says "Sorry, couldn't rename "298.1 GB Volume: Backup" to "Backup"

I tried e2label as well but when i type in the command, it goes through but when i check, it still says 298.1 GB Volume: Backup

Can this be changed for it to just say "Backup" ?

---

### Post by iris-n on 2007-12-16
I'm sure it can. Have you restarted after e2label?

---

### Post by dachinster on 2007-12-16
hey, thanks
that worked!
dint know i had to reboot linux so much
1st for my graphics driver and now this
ah well, im glad it is working

thanks again iris-n!

---

### Post by iris-n on 2007-12-16
You're welcome =)
Now it's indeed rare to have to restart a Linux system, but this time you're messing with something very deep; the system needs to know were his files lays.
In the case of common applications, you never have. Which is very annoying on Windows =D
If you could mark the thread as solved.

---

### Post by QwertyManiac on 2007-12-24
Can't we rename the "Filesystem" root partition to something else?

I tried **sudo e2label /dev/sda6 "Linux"** for it to show up as Linux in Nautilus but even on a reboot it remains the same "Filesystem". The e2label was successful cause tune2fs -l shows Linux as the Volume name for /dev/sda6 too.

```
tune2fs 1.40.2 (12-Jul-2007)
Filesystem volume name:   Linux
[......]
```

Is this a Nautilus fault or can I not rename the root partition at all?

(/dev/sda6 is my root partition "/")

---

### Post by QwertyManiac on 2008-01-03
No idea people?

I wanna change this "Filesystem" in the below picture to something else:
[[IMG]http://img165.imageshack.us/img165/7582/screenshotey4.png[/IMG]](http://imageshack.us)

---

### Post by acoustibop on 2008-01-03
See the Ubuntu Docuntation for help on this, QwertyManiac.

Is this a complete hard drive or partition on a hard drive, or a folder on a partition?  What filing system (i.e Ext3, NTFS etc) is it?  Do you want to change the label on the drive/partion/folder or do you want to just have your system recognise it under another name?

---

### Post by QwertyManiac on 2008-01-05
Thank you for replying acoustibop :)

I already mentioned in the first post of mine here that its my root partition "/". I think by default on all Ubuntu installations the root partition is named the same "Filesystem"?

And yes it is of the Ext3 type.

Changing the label didn't help, Nautilus still shows it as "Filesystem". And just system recognition as something else should do fine, since changing the label via e2label failed doing so.

Documentation is of no help. I searched quite a lot before posting here, all posts relevant to changing labels were mostly for NTFS drives or add-on Ext3 drives. None for the root one.

And again, I have already changed my label via "**e2label /dev/sda7 "Linux"**" where sda7 is my "Filesystem" icon in the shot above. Now even the output of** tune2fs -l** shows the Label set as "Linux" in it but Nautilus doesn't reflect that.

---

