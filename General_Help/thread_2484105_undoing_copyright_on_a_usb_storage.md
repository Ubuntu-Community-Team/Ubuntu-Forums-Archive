---
title: "undoing copyright on a usb storage"
date: 2023-02-17
forum: General Help
---

### Post by 2blue on 2023-02-17
For some reason I have burned the iso image of Ubuntu 22.10 in copyright mode. Is it a way to overwrite or format the USB drive? I have found some tutorials but I am a bit unsure of the identification of the drive in terminal. I rather proceed with delete the USB drive than something on the computer`s main ssd drive. 

Does it look like the last two entries in terminal sdb1 and sdb4 might be the usb drive? 


[IMG]https://ibin.co/w800/7CjmOd4jTYMT.jpg[/IMG]

---

### Post by TheFu on 2023-02-17
What's "copyright mode"?  Never heard of it.  Do you mean read-only mode?
If you use **df -Th** as the command, you'll be able to see what file systems are involved and see some human readable sizes, for each mounted file system.  

Understanding who Linux names different storage devices can be confusing at first. This link [Https://ubuntuforums.org/showthread.php?t=2467190&p=14059532#post14059532](Https://ubuntuforums.org/showthread.php?t=2467190&p=14059532#post14059532) should help to understand the terms.  All storage devices get device files for
[LIST]
[*]the entire drive
[*]each partition inside a drive
[/LIST]
Once you understand the differences, it becomes easy to work at either level, depending on what you need.  However, about 99% of the time, we'll work on partitions, not the how storage device (drive).  Be certain to thank MSFT for making people confused by using the wrong terms.

Another very useful command is:
```
lsblk -e 7 -o name,size,type,fstype,mountpoint,label
```
This shows how drives, partitions, and other storage objects relate to each other.  The last option "label" can be used to mount or you can replace or add "uuid" to use those random characters for mounting.  I much prefer labels, since I'm a human and having labels that make sense to me is easier.  I'm not a computer.

---

### Post by sudodus on 2023-02-18
Please tell us which tool and method you used to make the USB drive bootable with Ubuntu. We can guess, but need to know to give you reliable advice.

My guess is that you cloned from the iso file to the USB drive and have a read-only ISO9660 file system. If your USB drive is still physically healthy (and I think so), you can use some tool to make it a storage device again.

- It is very straightforward to use [mkusb](https://help.ubuntu.com/community/mkusb).
- If you want a tool with more options, you can use **[FONT=Courier New]gparted[/FONT]**, which is present in many live versions of Ubuntu and Ubuntu family flavours. It can easily be installed into installed systems.

---

