---
title: "Grub Error 24"
date: 2008-01-29
forum: General Help
---

### Post by redenex on 2008-01-29
Well, here I come again........ after all the trouble I had with Grub Error 17 a few months ago (Thanks again to Herman for helping me solve that).

Right now, I am not able to boot my Gutsy Gibbon, since it throws a **Grub Error 24**. I tried e2fsck, but it says the Super Block is beyond limits.

As I closed down my computer (just before this error starts showing), it said some files were forcible closed as Ubuntu was shutting down. Moreover, one problem I had faced before that was, when I tried to play some songs, it never opened, but whatever song file I selected was shown as locked in Nautilus. 


Any help appreciated! Some of the latest works that I have been doing have got caught in that disk.

---

### Post by danwood76 on 2008-01-29
To look up grub error codes go here:
[http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)
Its stage 2 errors you will be interested in.

```

24 : "Cannot boot without kernel loaded"

This error is returned if GRUB is told to execute the boot sequence without having a kernel to start.

```

Have you made any changes to your kernel image or menu.lst recently?
as it sound like it cant find the kernel image.

regards,
Danny

-- edir --

just re read your post and maybe its a failing hard disk?

---

### Post by redenex on 2008-01-29
I am unsure about it, but I doubt it could be a failing hard disk as well. Now, if it is a failed hard disk, is there any way I can retrieve data? :confused::(

---

### Post by danwood76 on 2008-01-29
Can you boot using the live CD?

If you can mount your hard disk and have a look for your kernel image and menu.lst in your /boot partition/directory.

If you cant mount it using the live CD then you do have problems, but seeing as grub loads it must be mounting at least the /boot portion of your drive.

regards,
Danny

---

### Post by redenex on 2008-01-29
Thank you Danny.

The BIOS is recognizing the hard disk, and error message comes when the grub tries to load.

I tried e2fck, but said the Super Block is beyond limit.

I shall try this again and post what I get. It is midnight for me and had a very tiring day, will try to get this up and running tomorrow. :KS

---

### Post by redenex on 2008-01-29
I ran e2fsck and here is the result:

```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v  /dev/hda1
e2fsck: Filesystem revision too high while trying to open /dev/hda1
The filesystem revision is apparently too high for this version of e2fsck.
(Or the filesystem superblock is corrupt)

/dev/hda1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


```

---

### Post by redenex on 2008-01-29
I am currently running ```
sudo e2fsck -b 32768 /dev/hda1
```

Will post the results as well.

---

### Post by Herman on 2008-01-29
Hello Redenex,
Here are some links that should be useful to you, [                      Running a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem"), that might not fix anything in your case, but is still worth a try and should at least give you more feedback about what exactly is wrong. (Maybe only the same feedback again, or maybe something usful, just try it anyway, it won't hurt)

If you just have a bad superblock, don't worry, there are lots of spare backups of the superblock, and you can easily replace the superblock with  one of the backups, [What to do if you have a bad ext3 superblock]("http://users.bigpond.net.au/hermanzone/p10.htm#superblock_restoration_frombackup").

This link might also be interesting, [How to take a look at your ext3 superblock]("http://users.bigpond.net.au/hermanzone/p10.htm#take_a_look_at_your_ext3_superblock").

You might want to run a check for badblocks in your hard disk,  [Running a check for bad blocks on your hard disk]("http://users.bigpond.net.au/hermanzone/p10.htm#bad_blocks_check"), 

You probabbly won't need this, but here is the link, just in case, [Recovering files from lost+found]("http://users.bigpond.net.au/hermanzone/p10.htm#Recovering_files_from_lostfound").

I have recently added a new feature in my website that might be interesting for you as well, [Check On Your Hard Disks With Smartmontools]("http://users.bigpond.net.au/hermanzone/p20.html#Check_On_Your_Hard_Disks_With").

I hope something in those links will help you, you are going to sleep when I am waking up, and when you wake up I will probably be at work. I will check back here when I can to see what is happening. Good luck with it, I hope your hard disk will be okay and you can get all your files back okay.

Regards, Herman :)

---

### Post by redenex on 2008-01-29
Thanks you for checking this out Herman. Infact my previous command worked. I believe my hard disk needs a replacement, seems like there are bad sectors. Once I got my computer booted, I also ran ```
sudo e2fsck -C0 -p -f -v  /dev/hda1
``` again, and it has sorted out the issues for me.

I guess it is high time I move to a new computer, this one is almost 5 years old.:guitar:

---

### Post by Herman on 2008-01-29
:) Okay, very good, redenex, well done! 5 years old is not too old for a computer, but they are making better computers now and selling them for less money than we could buy a computer for five years ago. The decision is up to you.

I replaced a hard disk in an old computer and it is still running well, the rest of the computer is almost ten years old now, although I also replaced a few other parts, so I cannot say that I have saved any money, but rather I have had fun and learned a little more about computers by playing with it. Here is my link about that one, it needed a new power supply too, [BookPC Gets Big Power Supply]("http://herman543.googlepages.com/bookpcgetsbigpowersupply2").

It's nice to have an older computer for a second computer and can very be useful for lots of different reasons.
One reason is it means we can have two monitors, and one can be on a web page with a how-to on it that we areable to look at and refer to while doing an operation in the other computer
My computers are connected with [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm") and that's often very handy as well.

Whatever you decide, good luck and have fun,
Regards, Herman :)

---

### Post by redenex on 2008-01-29
> **Herman said:**
> :) Okay, very good, redenex, well done! 5 years old is not too old for a computer, but they are making better computers now and selling them for less money than we could buy a computer for five years ago. The decision is up to you.

I agree. But for my business needs I was planning to buy a notebook, which I would be by mid-February. I was unsure if should keep this desktop. Will see.

ps: 2:15 AM here, and I haven't slept. Perhaps over excited to get back my data! hahaha Good day everyone!

---

