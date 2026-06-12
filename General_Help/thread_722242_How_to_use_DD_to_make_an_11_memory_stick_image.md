---
title: "How to use DD to make an 1:1 memory stick image"
date: 2008-03-12
forum: General Help
---

### Post by perixx on 2008-03-12
Hy folks!

Can somebody please confirm or give an alternate example, if the following commands will work to backup/restore all availible sectors from/to a memory stick (or any other drive)?

```
sudo dd if=/dev/SOURCEDRIVE of=/media/TARGET.img count=1
```

```
sudo dd if=/media/TARGET.img of=/dev/SOURCEDRIVE count=1
```

Thank you,

perixx

---

### Post by kuja on 2008-03-12
I've done it with hard drive partitions, Cd's, and DVD's, regular files, etc ...  but never with a flash drive, but i don't see why it wouldn't work for them too. You'll want to remove the count=1 part, because that will make it copy only the first 512B block.

---

### Post by munkyeetr on 2008-03-12
I just tried it on a 512 MB USB drive and while it showed successful on the command-line:
```

jon@ubuntu:~$ sudo dd if=/dev/sdg1 of=/media/usb.img
[sudo] password for jon:
1000711+0 records in
1000711+0 records out
512364032 bytes (512 MB) copied, 27.1162 seconds, 18.9 MB/s
jon@ubuntu:~$ sudo dd if=/media/usb.img of=/dev/sdg1
1000711+0 records in
1000711+0 records out
512364032 bytes (512 MB) copied, 95.6998 seconds, 5.4 MB/s

```

the "folders" put back on the drive, weren't folders, and when I click on them they disappear!

[IMG]http://i28.tinypic.com/2lctg6c.png[/IMG]

---

### Post by munkyeetr on 2008-03-12
UPDATE: After I unmounted the drive and remounted it, the folders were back to normal and  all appears as it was originally.

---

### Post by hyperair on 2008-03-12
Rule of thumb: NEVER leave a file system mounted when backing up or restoring an image of it.

---

### Post by munkyeetr on 2008-03-12
> **hyperair said:**
> Rule of thumb: NEVER leave a file system mounted when backing up or restoring an image of it.

Good to know! :KS

---

### Post by perixx on 2008-03-17
Hi guys! 

Sorry for the late answer... That sounds promising! Maybe I'll give it a try sometime, heard about making an image and restore that image to the re-formatted stick would normally bring back all data. It's but not that easy to correctly format a stick, from what I read... 

I was trying hard to get back at least SOME data from that borked stick - and actually I really could retrieve my (most important) files :)

I used the 'GetBackData' demo recovery program - it was one of the only 3 programs that seemingly found all lost files and folders - and the only one which let me really retrieve anything; since it's a demo, you normally wouldn't be able to save any found files with it.
But there's a trick: you can open any text-editable file with  your Windows texteditor and THEN save it from there! Maybe it's also possible to recover executables with a hex/binary editor - I haven't tried that...

Although it's very cumbersome to rename every saved file afterwards, it's REALLY better than nothing at all !! =)

Btw., good to know about the 'count=1' parameter! Thanks for your reply!


perixx

---

