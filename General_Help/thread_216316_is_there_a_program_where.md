---
title: "is there a program where"
date: 2006-07-15
forum: General Help
---

### Post by jaimz on 2006-07-15
I can transfer files from my windows partition to my linux partition?

I remember reading about such a program in some thread
but I can't find the thread

also, I have another quetion

I made another partition on my second hard drive
the partition was ext3
I thought that making that would allow me to have like an extra partition for storage when I'm on ubuntu
so I would be able to store my music and stuff to it
but when I tried to access it, it said it couldn't mount or something

so I was wondering if there's a way for me to be able to use two different partitions for ubuntu

I'm really considering switching to ubuntu and getting rid of windows 
but the fact that I still have so much stuff in my windows partitions is what keeps me from deleting it

thank you in advance for your help

---

### Post by aeiah on 2006-07-15
ive got 5 partitions i can access under linux. you shouldnt have a problem with the right guides. mine include a windows ntfs, 2 fat partitions, a /home and a /.

you should be able to mount your windows partition in ubuntu and access everything, and transfer things over if you wish. if your windows partition is NTFS then you wont be able to write to it, but you will if its a FAT partition.

sometimes ubuntu can be funny about mounting drives but try doing forum searches for 'fstab' and 'mounting ntfs' or 'mounting windows partition' etc. (fstab is a file that tells ubuntu what to mount when it boots, and you'll probably need to edit it in some way)

looking at howto's and threads relating to mounting drives should also help you with your additional ext3 partition problem.

see if simply going to system>administration>disks and mounting them all there helps. dont forget to set mount point folders in the 'access path' box

---

### Post by elettronicha on 2006-07-15
> **jaimz said:**
> I can transfer files from my windows partition to my linux partition?
Yes, you can. Just mount on the system your Windows partition in read mode. If you don't know how, just try searching the wiki the keyword "fstab" o "mount". ;)

> I made another partition on my second hard drive
the partition was ext3
I thought that making that would allow me to have like an extra partition for storage when I'm on ubuntu
so I would be able to store my music and stuff to it
but when I tried to access it, it said it couldn't mount or something

so I was wondering if there's a way for me to be able to use two different partitions for ubuntu

As above, try reading the official documentation of Ubuntu and searching the wiki.

Those are FAQ. 

Bye!

---

### Post by jaimz on 2006-07-15
ok thanks guys

but trying to go into the partitions, it says I don't have permission to go in them. ._.

I'll check up on the fstab thing

---

### Post by compwiz18 on 2006-07-15
Howdy

Try running (don't flame me too much for this...) **sudo nautilus** in the terminal, this should let you look at any partition you have mounted. JUST BE CAREFUL.  YOU CAN SCREW YOUR COMPUTER UP WITH THIS. As long as you don't edit/replace/delete files (creating them is safe though), you should be fine.

---

### Post by jaimz on 2006-07-15
> **compwiz18 said:**
> Howdy

Try running (don't flame me too much for this...) **sudo nautilus** in the terminal, this should let you look at any partition you have mounted. JUST BE CAREFUL.  YOU CAN SCREW YOUR COMPUTER UP WITH THIS. As long as you don't edit/replace/delete files (creating them is safe though), you should be fine.

ok thank you

---

### Post by Irony on 2006-07-15
No don't do that, do;

[PHP]gksudo nautilus[/PHP]

For graphical apps use gk. You will now be running with root privileges;

Then go to;
[PHP]
/mnt[/PHP]

Then make a folder called say;

[PHP]Windows[/PHP]

Now go to;
[PHP]
/etc[/PHP]

And open the file called;

[PHP]fstab[/PHP]

Now add a line;

[PHP]/dev/hda1       /mnt/Windows  ntfs    nls=utf8,umask=0222 0       0[/PHP]

Where hda1 will be whatever Windows is actually on (usually hda1 as it happens).

Now close the Nautilus. Then open a terminal and type;

[PHP]sudo mount -a[/PHP]

This will mount the new fstab file. Navigate your way with normal Nautilus to;

[PHP]/mnt/Windows[/PHP]

And you will see your Windows files.

---

### Post by jaimz on 2006-07-15
thank you!

that worked perfectly

just need to get my second hard drive to be mounted now too

---

### Post by jaimz on 2006-07-15
I got the second hard drive to be mounted - edit

---

### Post by Epperly on 2006-07-16
Irony: When I try that nothing shows up in the Windows folder... I've been trying to find a way to access my Windows hard drive but don't know how... can you help me?

---

