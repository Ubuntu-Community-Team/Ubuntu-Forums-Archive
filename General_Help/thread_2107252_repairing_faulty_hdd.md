---
title: "repairing faulty hdd"
date: 2013-01-21
forum: General Help
---

### Post by sirvinniei on 2013-01-21
hey,

I had ubuntu installed on my laptop.
I decided to add a boot partition.
I started up the live cd started gparted and tried to resize my main partition, but because it said it would take 7 hours I without thinking shut down my pc the wrong way.
Now ubuntu won't boot and I get a bios selection screen instead (showing a list of hdd, cd-drive etc.)
I tried reinstalling ubuntu but it gave me a error.
My question is is there a way to fix my hdd so I would be able to use it once again, I don't care about recovering previous data I just want the quikest way to fix errors on the hdd (the hd is still visible via gparted and i can even see partitions)

thanks

---

### Post by dannyboy79 on 2013-01-21
your statement, "I tried reinstalling ubuntu but it gave me a error" no one will be able to help if you don't tell us the specific error or problem.

here's a possible solution: make a gparted live cd, erase the drives partitions and partition table, wipe out the drive so it's unallocated space. then just shutdown the gparted live cd and boot up to an ubuntu cd to perform a new install.

i am baffled by the amount of threads i see where an ubuntu live cd can't perform an install because of problems like this ( people claiming a hard drive error but never very specific), the installer should be able to wipe out a drive if need be.

---

### Post by sirvinniei on 2013-01-21
sorry the error was error errno 5: a problem with the cd-drive or a faulty hdd. (I'm sure its the last one cause it was the partitions i was messing with)
will wiping the hdd not take a ridicoulous amount of time, because moving the partition or decreasing it in size did

---

### Post by rpm13 on 2013-01-21
> **sirvinniei said:**
> sorry the error was error errno 5: a problem with the cd-drive or a faulty hdd. (I'm sure its the last one cause it was the partitions i was messing with)
will wiping the hdd not take a ridicoulous amount of time, because moving the partition or decreasing it in size did

Ive found moving much slower than 'wiping' ie (re)partition.

If gparted works (and you are not interested in rescue) just erase all partitions with gparted (or parted) and reinstall

---

### Post by sirvinniei on 2013-01-21
wiped everything, still same error: errno 5: input/output error

---

### Post by howefield on 2013-01-21
Try running fsck on the drive, from the Live CD, open a terminal and type the following..

```
fsck /dev/sda1
```

assuming that the disk you want to check is sda1.

---

### Post by rpm13 on 2013-01-21
> **sirvinniei said:**
> wiped everything, still same error: errno 5: input/output error

Have you seen this:
[http://www.linuxquestions.org/questions/linux-newbie-8/errno-5-input-output-error-639355/]("http://www.linuxquestions.org/questions/linux-newbie-8/errno-5-input-output-error-639355/")

---

### Post by rpm13 on 2013-01-21
> **howefield said:**
> Try running fsck on the drive, from the Live CD, open a terminal and type the following..

```
fsck /dev/sda1
```

assuming that the disk you want to check is sda1.

It seems the error is at a lower than file system level, perhaps device level.

Can you try with parted rather than gparted?
[Yeah its a console app and more painful than gparted but also more solid]

---

### Post by sirvinniei on 2013-01-21
it says: fsck form util-linux 2.20.1
e2fsck 1.42 1.42 (29-nov-2011)
fsck.ext2: no such file or directory while trying to open /dev/sda1
possibly non-existent device?

which sounds kind of logical since i whiped the hdd

---

### Post by sirvinniei on 2013-01-21
> **rpm13 said:**
> It seems the error is at a lower than file system level, perhaps device level.

Can you try with parted rather than gparted?
[Yeah its a console app and more painful than gparted but also more solid]
im in parted, what commands should i use?

---

### Post by rpm13 on 2013-01-21
> **sirvinniei said:**
> im in parted, what commands should i use?

h for help (or '?')
then follow what you are told!
q for quit

mkpart is the main one
unit is also useful to talk in terms of GBs rather than bs!

---

### Post by sirvinniei on 2013-01-21
mkpart makes a partition
what do i need to put in for name?
and what kind of format?

---

### Post by dannyboy79 on 2013-01-21
are you sure the hard drive is any good? seriously, i haven't known anyone to have such issues with gparted not being able to format a hard drive.

if it were me, i would boot to a live cd, check exactly which hard drive it is you want to effect (make sure you use correwct device) and then issue the following to write zero's to it.

```
dd if=/dev/zero of=/dev/sda bs=1M
```

then once that's done, boot the computer to an ubuntu cd again and see if the install will work

---

### Post by sirvinniei on 2013-01-21
don't know if my hdd is any good, it was standard with my my laptop.
I'm 90% sure the problem is with my hdd because my bios also gives some kind of error message (which is unreadable because it gets away so fast)
I'm currently running the script you gave me.
How long should it take?
If all else fails I guess I will have to go to the shop I bought it and claim my warranty. But I'm not sure if I'll get waaranty since its not a problem caused by the production but a problem caused by me

---

### Post by dannyboy79 on 2013-01-21
how large is the hard drive? it depends on large it is on how long it will take. you can view the status of it by issuing the following command in another terminal window and it'll update you of dd's status every 10 seconds.
```
watch -n 10 killall -USR1 dd
```

---

### Post by sirvinniei on 2013-01-21
its 750 gb
btw is there any way to stop my pc from suspending so i wont have to watch it all the time?

---

### Post by dannyboy79 on 2013-01-21
hmmm, are you running a gparted live cd? or what OS are you running? it should be within the admin settings for power management but I wouldn't think a live cd would have suspend set by default but I am not sure

---

### Post by rpm13 on 2013-01-21
> **sirvinniei said:**
> hey,

I had ubuntu installed on my laptop.
I decided to add a boot partition.
I started up the live cd started gparted and tried to resize my main partition, but because it said it would take 7 hours I without thinking shut down my pc the wrong way.


I think youve just (!) knocked off your partition table.
Check in gparted-> device -> make partition table

As for parted (more stable), the equivalent command is mklabel: COuld be msdos or gpt, try both. If the current partition table is not quite gone, the p (short for print) command of parted will tell you which it is

Generally for parted, theres more help on a command with help, eg
```
help mkpart
```

Generally for mkpart it is
```
mkpart A B C
```
A is logical or primary or extended
B should be the top of what p(rint) shows
C should be B + size you want
Before you start partitioning:
```
unit GB
```
makes life easier

Also remember that for old-fashioned (msdos) partition tables you need to make 3 primary, fourth is extended and then (5th) onwards are logical

---

### Post by sirvinniei on 2013-01-22
finished the script and I'm still having the same error when trying to install

---

### Post by dannyboy79 on 2013-01-22
something is very wrong. are you sure your live cd or live usb stick is good? did you check the MD5 sum of the iso after you downloaded it?

installer should be able to install ubuntu on hard drive whether it has a partition table or not. heck, it can even shrink down NTFS partitions and install ubuntu along side windows. I am not sure why you are having these issues.

---

### Post by rpm13 on 2013-01-22
> **sirvinniei said:**
> finished the script and I'm still having the same error when trying to install

pls try in parted
```
mklabel msdos
q

```

What does it say (if anything)?
If nothing try install again.

Should add:
Even more stable than parted is fdisk (and even harder to use!)

---

### Post by sirvinniei on 2013-01-22
Sorry for the inconvenience,
it turned out to be a uefi problem
still a lot of thanks to you:D

gr.

---

### Post by dannyboy79 on 2013-01-22
> **sirvinniei said:**
> Sorry for the inconvenience,
it turned out to be a uefi problem
still a lot of thanks to you:D

gr.

WOW......i can't believe none of use thought of that. lol

---

