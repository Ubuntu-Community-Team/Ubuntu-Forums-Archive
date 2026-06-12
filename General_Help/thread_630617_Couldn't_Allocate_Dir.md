---
title: "Couldn't Allocate Dir"
date: 2007-12-03
forum: General Help
---

### Post by Adimoolah on 2007-12-03
Hello how is everybody doing, well I hope.

I am having a problem, obviously, this is the help page, hehe.

I just started using ubuntu, my first day.  I am having a problem using my azureus bit torrent client.  Everything works fine, but I am trying to us my external 80 gig hard drive to save my files to, and when I try to do that I get an Errno 30 Couldn't Allocate Dir?

What does this mean and how do I allocate the dir?

---

### Post by metalheart on 2007-12-03
Make a new directory **dirname** on the disk and

```
chown user:user /media/disk/dirname
```

**user** is your Ubuntu username.

---

### Post by Adimoolah on 2007-12-03
Okay, I tried that code in the terminal replacing user with my username and it says no such file or directory?

---

### Post by jfinkels on 2007-12-03
You have to make the directory first like this:```
mkdir /media/disk/*dirname*
```where *dirname* is the name that you want to use for the directory. Of course, your disk may be mounted at some other location, perhaps */media/disk1* or */media/sdb1* or something.

---

### Post by Adimoolah on 2007-12-03
Okay, it's official, I am completely lost.  I don't even know how to do that, or what you are talking about.  I don't know where my external drive is mounted or even how to find that information.  I thought if it was mounted, then it would be already working, right?  

I don't understand why ubuntu just doesn't recognize the external drive, when I used xp, I didn't need to do anything,  it just recognized it, no problems.  I wanted to try ubuntu, because vista crashed on me and I got fed up, but I just don't have the free time to learn all of this stuff, ubuntu is not very user friendly.  

I wanted to give ubuntu a fair shot, but it seems as though this system is setup for those who are more computer savvy than myself, I just find using all these codes to be very confusing.

---

### Post by atlfalcons866 on 2007-12-03
he means you have to go to terminal 
applications>accesories>terminal then enter the commands

---

### Post by metalheart on 2007-12-03
Your external drive should be mounted in /media/disk

You may need administrator access to create directory on this disk. You can do this

```
sudo mkdir /media/disk/dirname
```

Then change user rights to this directory

```
sudo chown user:user /media/disk/dirname
```

Sorry, I was a little shallow on the subject.

---

### Post by jfinkels on 2007-12-03
> **Adimoolah said:**
> 
I wanted to give ubuntu a fair shot, but it seems as though this system is setup for those who are more computer savvy than myself, I just find using all these codes to be very confusing.

Sorry for the intimidating commands. Often in the forums, people will instruct others to type commands into the terminal (Applications > Accessories > Terminal) because it is simpler than trying to explain what to do using a graphical user interface.

When you plug in your external drive, it must be "mounted" before it can be read from or written to. The process of mounting allows you to access files stored on the drive by navigating to a location in the directory hierarchy. By default, Ubuntu should recognize your drive, automatically mount it, and put a "link" to it on your desktop. If it doesn't show up automatically, then you may have to go to the terminal and try to mount it manually by using the "mount" command.

(Note: take a look here and in the other links in my signature for some great introductory information: [http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows) )

Now, plug in your external drive, open the terminal, and make sure it is plugged in. To view all disks connected to your system and partitions on those disks, type the following in the terminal:```
sudo fdisk -l
``` (that's a lowercase L). Now type your password and press enter. Now you will see something like this:```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            7193        9173    15912382+  83  Linux
/dev/sda2            9174       12161    24001110    5  Extended
/dev/sda3   *        4963        7192    17912475   83  Linux
/dev/sda5           11919       12161     1951897+  82  Linux swap / Solaris
/dev/sda6            9174       11918    22049149+  83  Linux

Partition table entries are not in disk order

```

You will be able to see another disk, named something like /dev/hdb or /dev/sdb (disks on Linux systems are named in the form /dev/hd*x*). A disk can have several partitions, each one has a number, which is appended to the end of the disk name to specify it, so on my system, my Ubuntu 7.10 installation is on partition /dev/sda3. You will need to determine which partition you need to mount.

Before mounting your partition, you must make a directory for it. To do that type:```
sudo mkdir /media/mydisk
```and type your password and press enter.

To mount the drive, type the following:```
sudo mount /dev/hd*x**#* /media/mydisk
``` Then your disk partition will be mounted at /media/mydisk. To change the ownership of the directory in which the partition is mounted, type the following:```
sudo chown *username*:*username* /media/mydisk
```

---

