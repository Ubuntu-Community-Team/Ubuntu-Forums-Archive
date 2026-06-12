---
title: "Why Can I Not Add a Partition onto My Device?"
date: 2018-01-12
forum: General Help
---

### Post by joseph-hardrock on 2018-01-12
I made a device on /dev directory called as /dev/sdb2. I am trying to make a partition on this device. But I can't do that. When I try to run this command:
mkpart primary 123 4567
it gives an error about primary. However I can run this command with filesystem things. For example:
mkpart ext4 123 4567
I can't do that, because can I just add a partition onto a disk? For example, /dev/sda. Am I trying to add a partition onto a partition?

---

### Post by sudodus on 2018-01-12
Please run the following commands (with your drive /dev/sdb connected),

```

sudo lsblk -f
sudo lsblk -m
df
sudo parted -ls

```

and post the result in a reply. It will help us help you.

[hr][/hr]
Please put the output of the commands within [noparse]```
tags
```[/noparse] to make it easier to read: Click on the red button **[COLOR="#FF0000"]Go Advanced[/COLOR]**, mark the text and click on the **#** icon above the editing window (or do it manually), like this:

[noparse]```

your output line 1
line 2
line 3
...

```[/noparse]

Notice that you can mark (press the left button while moving the cursor) and paste (press the middle button or wheel to paste) from a terminal window to the editing box of Ubuntu Forums.

---

### Post by yancek on 2018-01-12
Never seen that command before myself.  You might try posting some information on the drive partitions which you should be able to do from a terminal with either command below.  Someone should then be able to advise you.

```
sudo fdisk -l
sudo parted -l
```

Lower case Letter L in both commands.

---

### Post by Dennis N on 2018-01-12
You don't give information on existing partitions, so hard to tell what the problem is. Maybe you have already reached the limit on the number of primary partitions (which is 4 for MS-DOS partitioning). Or perhaps your specified start or end fall within another partition.

---

### Post by joseph-hardrock on 2018-01-13
Yes, you are right. When I try to add a partition it gives this error:
Too many partitions. 
Anyway, I will try commands that other users said, and I will post the result into here. Thank all of you.
@Dennis N

---

### Post by joseph-hardrock on 2018-01-13
> **sudodus said:**
> Please run the following commands (with your drive /dev/sdb connected),

```

sudo lsblk -f
sudo lsblk -m
df
sudo parted -ls

```

and post the result in a reply. It will help us help you.

[HR][/HR]
Please put the output of the commands within [noparse]```
tags
```[/noparse] to make it easier to read: Click on the red button **[COLOR=#FF0000]Go Advanced[/COLOR]**, mark the text and click on the **#** icon above the editing window (or do it manually), like this:

[noparse]```

your output line 1
line 2
line 3
...

```[/noparse]

Notice that you can mark (press the left button while moving the cursor) and paste (press the middle button or wheel to paste) from a terminal window to the editing box of Ubuntu Forums.

I am sorry to posting late, but I have jobs to do.
```

[COLOR=#ff0000]sudo lsblk -f[/COLOR]

```
 [ATTACH=CONFIG]278175[/ATTACH]
```

[COLOR=#ff0000]lsblk -m[/COLOR]

```
[ATTACH=CONFIG]278176[/ATTACH]
```

[COLOR=#ff0000]df[/COLOR]

```
[ATTACH=CONFIG]278177[/ATTACH]
```

[COLOR=#ff0000]sudo parted -ls[/COLOR]

```
[ATTACH=CONFIG]278178[/ATTACH]

---

### Post by sudodus on 2018-01-13
This seems to be vmware drive. Is it a virtual drive, and are you running a virtual machine?

You wrote in your first post, that you are trying to create partitions on /dev/sdb (drive 'b', the second one). But I cannot see any /dev/sdb, only /dev/sda, which contains the running system. Please explain or make a new try, where you include /dev/sdb in the output.

---

### Post by HermanAB on 2018-01-14
By the sounds of it, you are confused regarding devices, partitions, file systems and directories.

You cannot 'create' a device.  A device is a piece of hardware (You need a factory...).

/dev is a system directory which lists the device handles.

/dev/sda is a handle to a block device, the first hard disk.

Device sda can be partitioned into sda1, sda2... which will show up as device handles /dev/sda1, /dev/sda2...

Each partition can then be formatted with a filesystem and the file system can have directories and finally, you can save files in directories.

---

### Post by coffeecat on 2018-01-14
@joseph-hardrock, please do not post terminal output like this:

> **joseph-hardrock said:**
> ```

[COLOR=#ff0000]sudo lsblk -f[/COLOR]

```
 [ATTACH=CONFIG]278175[/ATTACH]


Little snipped bits of screenshots of a terminal are hard to read, and members helping you cannot easily quote any of the output if they need to.

sudodus asked you to:

[quote=sudodus]Please put the output of the commands within ```
tags
``` to make it easier to read:[/quote]

It's easy to copy paste from the terminal to your post. Sudodus describes one way, another is to highlight the terminal output that you wish to paste with the mouse, then ctrl-shift-c to copy. Then paste in the normal way into the message editor and add code tags.

---

### Post by joseph-hardrock on 2018-01-14
> **coffeecat said:**
> @joseph-hardrock, please do not post terminal output like this:



Little snipped bits of screenshots of a terminal are hard to read, and members helping you cannot easily quote any of the output if they need to.

sudodus asked you to:



It's easy to copy paste from the terminal to your post. Sudodus describes one way, another is to highlight the terminal output that you wish to paste with the mouse, then ctrl-shift-c to copy. Then paste in the normal way into the message editor and add code tags.

I will consider this situation for my next post.

---

### Post by joseph-hardrock on 2018-01-14
> **HermanAB said:**
> By the sounds of it, you are confused regarding devices, partitions, file systems and directories.

You cannot 'create' a device.  A device is a piece of hardware (You need a factory...).

/dev is a system directory which lists the device handles.

/dev/sda is a handle to a block device, the first hard disk.

Device sda can be partitioned into sda1, sda2... which will show up as device handles /dev/sda1, /dev/sda2...

Each partition can then be formatted with a filesystem and the file system can have directories and finally, you can save files in directories.
[COLOR=#000000]But I can make devices with this command:[/COLOR]
```
[COLOR=#ff0000]mknode /dev/sdb1 b 8 1[/COLOR][COLOR=#000000]
[/COLOR]
```

---

### Post by The Cog on 2018-01-14
Coffecat is right. Is is much better for those helping out if you post copy/pasted text rather than screenshots. Although I appreciate that this may be difficult with a virtualbox console (Can't remember if copy/paste from virtualbox console is possible). Either way, do please also include the command you entered so we can spot any errors in the input.

To expand on HermanAB's comment - items in the /dev/directory are not real files, they are created by the operating system as it boots, and they generally correspond with hardware that has been found during boot.  Much like COM1, COM2, LPT1 etc in DOS. In your case there is no /dev/sdb there, because no second hard disk was discovered during boot. There is nothing to be gained by trying to create these by command - even if you succeed they will be functionally broken as there is no real hardware behind them to manipulate.

---

### Post by joseph-hardrock on 2018-01-14
> **The Cog said:**
> Coffecat is right. Is is much better for those helping out if you post copy/pasted text rather than screenshots. Although I appreciate that this may be difficult with a virtualbox console (Can't remember if copy/paste from virtualbox console is possible). Either way, do please also include the command you entered so we can spot any errors in the input.

To expand on HermanAB's comment - items in the /dev/directory are not real files, they are created by the operating system as it boots, and they generally correspond with hardware that has been found during boot.  Much like COM1, COM2, LPT1 etc in DOS. In your case there is no /dev/sdb there, because no second hard disk was discovered during boot. There is nothing to be gained by trying to create these by command - even if you succeed they will be functionally broken as there is no real hardware behind them to manipulate.

No problem about copying something from terminal. I just think that screenshots will be better. But it seems not.

I understand how the /dev directory works. There is something called as udev. Before udev we have to make a device with the command that I wrote to my last post. And after that we can connect devices to our system. It means we have to manage devices own ourselfs. But there is no more need to do it because of udev. My mistake is that I should connnect a disk after making my device. 
Thank you all. :D(By the way, I hope it is the correct understanding.)

---

### Post by joseph-hardrock on 2018-01-14
Could any problem occur if I try to add partition onto my /dev/sda? I will try it in my virtual machine that has not any important information.

---

### Post by The Cog on 2018-01-14
Sorry, I didn't mean to talk down to you.

I have never manually created a /dev entry. If you connect another disk, the /dev/sdb entry should appear without your intervention. As for creating another partition /dev/sdb2, you would do that by writing a new version of the partition table contents to /dev/sdb. Again, I would expect /dev/sdb2 to appear once the partition table says it's there.

I have to say that the idea of manually creating /dev entries seems completely alien to me. I formed the impression that you were new to Linux and had some wrong ideas about how to do things. Maybe you are way ahead of me instead.

---

### Post by The Cog on 2018-01-14
I see you want to delete a post. You can't. You can edit it (as you have done). 

To get it deleted, use the !Report Post button and fill in the messagebox as to why you are reporting it, e.g. "please delete". The moderators will then oblige - it's a common occurrence and they don't mind being asked.

---

### Post by joseph-hardrock on 2018-01-14
> **The Cog said:**
> Sorry, I didn't mean to talk down to you.

I have never manually created a /dev entry. If you connect another disk, the /dev/sdb entry should appear without your intervention. As for creating another partition /dev/sdb2, you would do that by writing a new version of the partition table contents to /dev/sdb. Again, I would expect /dev/sdb2 to appear once the partition table says it's there.

I have to say that the idea of manually creating /dev entries seems completely alien to me. I formed the impression that you were new to Linux and had some wrong ideas about how to do things. Maybe you are way ahead of me instead.

I am new in linux. I am trying to learn. Since my mother language is not English, it is hard to understand linux courses easily for me. Also, thank you for telling deleting process.

---

### Post by The Cog on 2018-01-14
Welcome to Linux and the community. I'm sure you will find it interesting.

If you want to add a partition to an existing hard disk, as I said, the thing to do is to edit the partition table. This can be done with parted (a command line app) but I have never used that - there is a graphical tool called gparted. You may need to install it first: **sudo apt install gparted**.

---

