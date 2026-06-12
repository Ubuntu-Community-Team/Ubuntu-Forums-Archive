---
title: "How do I change the permissions of a file?"
date: 2007-05-24
forum: General Help
---

### Post by Zavie A. on 2007-05-24
i recently deleted Windows XP and installed Ubuntu Feisty Fawn. And everything was wonderful until just now.

I tried to delete some old programs on my second drive that don't work with Ubuntu and were just taking up space and its telling me i cant do this because i don't have "permissions"

It uses an NTFS filesystem.

IS THERE ANY WAY FOR ME TO CHANGE THE PERMISSIONS OF A FILE?

im almost in tears...PLEASE HELP!

---

### Post by benanzo on 2007-05-24
You probably need to be root in order to delete them.  Instead of telling you how to do it from a terminal with 'sudo', you can just launch Nautilus (the file browser) as root and navigate to those files and delete them normally:

Open and terminal **Applications - > Accessories -> Terminal** and type:
```
sudo nautilus
```

---

### Post by Churnd on 2007-05-24
> **Zavie A. said:**
> It uses an NTFS filesystem.

Did you enable write support for NTFS?  This isn't turned on by default, and could be why you don't have "permission".

---

### Post by Znupi on 2007-05-24
```

sudo apt-get install ntfs-3g

```
**Applications -> System Tools -> NTFS Configuration Tool -> Enable write support for internal device -> OK**

That should do it.

**Edit:** About changing permissions...
```

man chmod

```
It's really confusing at first, but if you read carefully you'll get it. ;) (I still have to look through the manpage when I want to use it, I just can't remember the numbers, lol)

---

### Post by Zavie A. on 2007-05-24
ok...

ive tried the 'sudo nautilus' command

and the files i want to delete dont show up :S the only files that i can see are the ones i can alredy control

---

### Post by stchman on 2007-05-24
> **Znupi said:**
> ```

sudo apt-get install ntfs-3g

```
**Applications -> System Tools -> NTFS Configuration Tool -> Enable write support for internal device -> OK**

That should do it.

**Edit:** About changing permissions...
```

man chmod

```
It's really confusing at first, but if you read carefully you'll get it. ;) (I still have to look through the manpage when I want to use it, I just can't remember the numbers, lol)

When ntfs-3g is installed then anyone can do anything assuming the defaults is used in the fstab.

---

### Post by Zavie A. on 2007-05-24
:D i got it!

Znupi's way seems to be working

thank you all!

---

### Post by alchemy101 on 2007-05-25
I'm having problems with the instructions provided. I run the terminal commands, but no selection pops up under application/system. It's just automatix, nothing about ntfs. And i still can't make/delete anything on my two ntfs drives. :(

I get this:
marcus@marcusubu:~$ sudo mount -a
fusermount: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/hdb1 (Vista)

The line in fstab reads as follows
/dev/sda1 /media/Vista ntfs-3g defaults,locale=en_US.utf8   0    0
/dev/hdb1 /media/SATA320 ntfs-3g defaults,locale=en_US.utf8   0    0

The top line is a disk i have done exactly the same for - and it works fine.
Where's the problem?

---

### Post by Znupi on 2007-05-25
Try
```

gksudo ntfs-config

```
If that doesn't work, install ntfs-3g by following the intructions in my previous post.

---

### Post by alchemy101 on 2007-05-25
No  joy. I have followed your instructions to the letter.

---

### Post by Znupi on 2007-05-25
Have you tried running ntfs-config? What happened?

---

### Post by alchemy101 on 2007-05-25
It only gave me the option to mount the other partition on this drive. It dosen't see my other NTFS drives. One of them is now fully mounted (via your instructions) so that i can read/write it just fine on nautilus. The other refuses to mount via the same means (previous error message).

:(

---

### Post by moljac024 on 2007-05-25
You need to install both ntfs-3g and the ntfs-config. You can do it with synaptic, it's easier....

Also, if you're planning to switch to linux completely it would be a good idea to reformat your ntfs partitions to something linux can handle(like ext3), ntfs can cause a lot of trouble. I speak from experience on this one...

---

### Post by alchemy101 on 2007-05-26
You need to install both ntfs-3g and the ntfs-config. You can do it with synaptic, it's easier....

-I have installed both of these - hence why one of my two drives is working perfectly :)

Also, if you're planning to switch to linux completely it would be a good idea to reformat your ntfs partitions to something linux can handle(like ext3), ntfs can cause a lot of trouble. I speak from experience on this one...

- I wish i could. But, i still have to dual boot with windows for some of my critical work related applications, and i'd prefer to be able to swap between operating systems and read my files on both.


Is there any way i can rectify this? I've tried the command like 'makedir' equivelent command, but i get the previous error (previous post) when i try to actually mount the volume.

This, and ubuntu's dual screen LACK of support are my only problems. I wish i could fix it and make the switch permanent!

---

