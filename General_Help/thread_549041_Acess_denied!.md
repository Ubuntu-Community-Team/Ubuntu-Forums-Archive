---
title: "Acess denied!"
date: 2007-09-12
forum: General Help
---

### Post by bjmax31 on 2007-09-12
HI! i am new to these forums  hello to everybody!
I am new to linux I have high hopes for ubuntu though!:)

Except for this really annoying problem!
I can not acess any content on my drives what so ever:(

when i click on the drive it gives me this cryptic useless error

Unable to mount the selected volume

error: device /dev/hda1 is not removable

error: could not execute pmount


what does this mean? why don't things just work?

and if I edit any permissions all i get is

the permissions could not be changed:(
Sorry, couldn't change the permissions of. . .  ect

I feel like i'm locked out of my own machine! :(

can somebody please steer me in the right direction!

---

### Post by Soarer on 2007-09-12
It's difficult to know how to answer this, as the remedy might cause more trouble than the problem :(

There are some files you (as a user) shouldn't own - they should be owned by 'root' so you don't overwrite them accidentally, leading to borking your system.

However, to change the permissions or ownership of files you don't own, you need to use 'sudo' before the command.

Thus, for any files you need to own (essentially those in '/home/myusername' folder, you can do (in a terminal):

```
sudo chown -R myusername /home/myusername
```

which will make myusername the owner of all files & directories in /home/myusername.

The system will ask for your password (myusername's password) to ensure you realise that you are doing something potentially hazardous.

HTH.

---

### Post by bjmax31 on 2007-09-12
so i need your username to acess my files?

---

### Post by Maestro23 on 2007-09-12
> **bjmax31 said:**
> so i need your username to acess my files?

The username that you created when you installed Ubuntu.

---

### Post by bjmax31 on 2007-09-12
username@username-desktop:/media$ sudo chown -R username /home/username@username-desktop:/media$

tried to acess my disk again only for that error to pop back up!

---

### Post by Soarer on 2007-09-12
> **bjmax31 said:**
> username@username-desktop:/media$ sudo chown -R username /home/username@username-desktop:/media$

tried to acess my disk again only for that error to pop back up!

What error?

the command you need is:


```
sudo chown -R username /media
```

by the look of it. A few more details would help - it's hard to read your mind from here :)

---

### Post by K.Mandla on 2007-09-12
I'm a little confused, but if you're trying to mount or unmount /dev/hda1, that might be your root system partition. Ubuntu usually won't let you unmount the system partition, because it's using it.

What does this show?

```
sudo fdisk -l
```
That's a lowercase L at the end, by the way. It's not a number 1.

---

### Post by bjmax31 on 2007-09-12
I have 2 hard drives (1 with 2 partitions) i can mount them via command line (don't think it's a kernal problem) even with the drives mounted i can NoT acsess the content of my drives ( I am the only user of this machine BTW.)  and this is a fresh install

Error pops up:

Unable to mount the selected volume

error: device /dev/hda1 is not removable

error: could not execute pmount


anyway i can get rid of erorr???

please!!!!:(

---

### Post by Belinrahs on 2007-09-12
> **bjmax31 said:**
> I have 2 hard drives (1 with 2 partitions) i can mount them via command line (don't think it's a kernal problem) even with the drives mounted i can NoT acsess the content of my drives ( I am the only user of this machine BTW.)  and this is a fresh install

Error pops up:

Unable to mount the selected volume

error: device /dev/hda1 is not removable

error: could not execute pmount


anyway i can get rid of erorr???

please!!!!:(

It looks like you are trying to dismount /dev/hda1... "error: device /dev/hda1 is not removable"

I might be wrong but wouldn't that type of action trigger a response that something isn't removable?

---

### Post by gam3r4eva on 2007-09-12
What command are you trying to use to mount/unmount the drive?

As stated above, please post the output of "sudo fdisk -l"

---

### Post by kennyS on 2007-09-12
I was looking for *exactly* this issue: I also can see my other (WinXP, NTFS)  partitions in File Manager, but I'm prohibited from accessing them -- and something has changed since yesterday, because I *was* able to access them.:confused:

What command or configuration setting will allow me to access these files again?

Here is the the output of the fdisk command:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4825    38756781    7  HPFS/NTFS
/dev/sda2           13718       19457    46106550   83  Linux
/dev/sda4            4826       13717    71424990    5  Extended
/dev/sda5            4826        4980     1245006    7  HPFS/NTFS
/dev/sda6            4981        8897    31463270+   7  HPFS/NTFS
/dev/sda7            8898       13466    36700461    7  HPFS/NTFS
/dev/sda8           13467       13717     2016126   82  Linux swap / Solaris

Partition table entries are not in disk order
```Thanks in advance,
kennyS

---

### Post by Belinrahs on 2007-09-12
kennyS, I believe you need to mount the ntfs partitions with Terminal

Back on Dapper it auto-mounted my NTFS partitions automatically with a few packages from the repository, called ntfs-progs and ntfstools. That was a while ago of course...

---

