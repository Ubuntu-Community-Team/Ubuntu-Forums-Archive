---
title: "Ubuntu 14.04 doesn't mount drives"
date: 2014-10-19
forum: General Help
---

### Post by vj2 on 2014-10-19
[FONT=tahoma]Hey guys i recently installed **Ubuntu 14.04** on side of **Windows 8** and right now i can't even mount my drives on **Ubuntu 14.04** i can't access that drives it gives an error saying that it cannot mount.[/FONT]

[FONT=tahoma]Expecting fast replies [/FONT]:)

[FONT=tahoma]Here is the Picture of the error attached. [/FONT]

---

### Post by ajgreeny on 2014-10-19
Did you turn off fast-boot, or whatever it is called in Windows?

If you don't do that the disk will be in a state of hibernation and therefore flagged as still being used.

See:-
[http://askubuntu.com/questions/384884/unable-to-mount-windows-partition-fast-boot-is-already-off-still-get-the-pro](http://askubuntu.com/questions/384884/unable-to-mount-windows-partition-fast-boot-is-already-off-still-get-the-pro)
[http://askubuntu.com/questions/452071/why-disable-fast-boot-on-windows-8-when-having-dual-booting](http://askubuntu.com/questions/452071/why-disable-fast-boot-on-windows-8-when-having-dual-booting)

---

### Post by vj2 on 2014-10-20
[FONT=tahoma]Right now i can't boot my **Windows 8** because i got one file corrupted and i keep getting an error and it continuously restarts on a loop so at last installed **Ubuntu 14.04** alongside of **Windows 8**. [FONT=tahoma][FONT=tahoma]So is there anything that i should do to open my drives in **Ubuntu** since my **Windows** doesn't boot.[/FONT][/FONT]
[/FONT]

---

### Post by Bucky Ball on 2014-10-20
Please attach large pics using the paperclip icon in 'Go Advanced' or 'Adv Reply'. 

Did Windows shutdown correctly or crash?

What disks are not mounting? Internal and/or external? Do you mean partitions are not mounting? Ubuntu is booting fine, though? Are the partitions that aren't mounting on the same drive as Ubuntu?

Are the non-mountable partitions NTFS or EXT4 or something else?

* Also what ajgreeny mentioned ...

---

### Post by yancek on 2014-10-20
> [FONT=tahoma]Right now i can't boot my **Windows 8** because i got one file corrupted and i keep getting an error and it continuously restarts on a loop[/FONT]

Hopefully, someone here will be able to help but given the situation you posted above, you might be better off going to a windows forum and asking how to resolve whichever file got corrupted and how it might be repaired.  Ubuntu or any Linux is not going to be able to repair that.  If you have data on it, you should be able to mount it read-only as mentined in the error and get the data off but that won't help with your windows boot problem.

---

### Post by nerdtron on 2014-10-20
> **vj2 said:**
> [FONT=tahoma]Right now i can't boot my **Windows 8** because i got one file corrupted and i keep getting an error and it continuously restarts on a loop so at last installed **Ubuntu 14.04** alongside of **Windows 8**. [FONT=tahoma][FONT=tahoma]So is there anything that i should do to open my drives in **Ubuntu** since my **Windows** doesn't boot.[/FONT][/FONT]
[/FONT]

Boot into the Windows 8 DVD (or USB if you have one) and then launch the startup repair of windows. There's a big chance that windows will repair its boot loop problems. Downside will be grub will be erased.

---

### Post by vj2 on 2014-10-20
Windows did shut down it was a crash.
Internal HD are not mounting up and external HD are mounting and working though.
Non mountable partitions are NTFS.

---

### Post by Bucky Ball on 2014-10-20
> **vj2 said:**
> Windows did shut down it was a crash.

Does this mean it was a crash and not a clean shutdown of Windows? If that is the case, the NTFS drives have been left open and not unmounted from Windows which is probably why they're not mounting. I'm presuming the external drives weren't plugged in and switched on when Win crashed?

Try this in a terminal, from [HERE]("http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation"):

```
sudo ntfsfix /dev/sdXY
```

where XY is the partition. ex: sda2 or sdb1

---

### Post by vj2 on 2014-10-20
Yes it was a crash not a clean shutdown.
Nope external drives were not plugged in at the time of crash.
Now how do i mount my drives in Ubuntu.
Is there any way or should i disable the fast boot option(If so how do i disable it).

---

### Post by Bucky Ball on 2014-10-20
Did you read my last post? I gave you something to try there. Your internal drives probably have a hibernation flag so they are not closed, just sleeping.

Go into the BIOS to disable Fastboot from memory.

---

### Post by vj2 on 2014-10-20
I tried that command:> sudo ntfsfix /dev/sdXY
It worked and it is mounting now.
Thanks for the help man.

---

### Post by nerdtron on 2014-10-20
> **vj2 said:**
> I tried that command:
It worked and it is mounting now.
Thanks for the help man.

*mindblown*

I didn't think linux can scan/clean hibernated window drives :guitar:

---

### Post by Bucky Ball on 2014-10-20
> **vj2 said:**
> I tried that command:
It worked and it is mounting now.
Thanks for the help man.

Excellent news! Please mark the thread as solved by following the second link in my thread, enjoy and good luck. ;)

@nerdtron: Yea, never heard of it myself. Who woulda thunk it???

---

