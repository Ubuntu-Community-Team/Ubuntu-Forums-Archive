---
title: "DD image drive to new drive. Okay to leave symbolic links to a data partition?"
date: 2015-08-16
forum: General Help
---

### Post by mikodo on 2015-08-16
Hi.

I need to replace my only internal drive, (not sounding well). In it I have a second partition that holds my data, that mounts by /etc/fstab the  /mnt/data partition and is symbolically linked to my Xubuntu OS's ~/. (everything on the same drive ).

I want to put in a larger second drive in the computer, and use dd to image the original drive to the newer/larger second drive. Then, destroy the original drive.

I will use this, as outlined here by TheFu in post #2, to image the whole present drive as a guide:  [http://ubuntuforums.org/showthread.php?t=1929671](http://ubuntuforums.org/showthread.php?t=1929671)

Questions.

 Can I leave the symbolic links, to the fstab mounted /mnt/data partition and expect the symbolic "data" links to work, like on the replaced drive?

Would I need to format the new disk similarly, as Ext4 file system like the original  drive, before using dd or, will dd do that too?

If not, I am going to a fresh install on it, and start over. (data is backed up on two usb nodes).

I will not use Partimage, Partclone, Clonezilla, FSArchiver or, the likes. Maybe later,  when I have more time, I might investigate these.

Thank you.

---

### Post by mikodo on 2015-08-16
Thank you, for all that took the time to read that post. Especially, anyone who may respond.

I think I am going to install a new drive, and reinstall the OS.

I can use the experience bringing my data from backups and applying it in the /mnt/data partition and symbolically linking again to a new install.

It would give me more confidence in my backup scenarios. If, I have problems, now is the time to learn what has to be done, to do it right. Not, when a failed disk happens and, I am possibly more pressed for time.

Thanks, again.

---

### Post by oldfred on 2015-08-16
I am not a fan of dd as its nickname is Data Destroyer.
Too many users make a typo and then permanently destroy lots of data.

I do prefer clean installs, as then you also have a major houseclean. 

I typically have other Ubuntu installs just to see what new install looks like. After several I realized my recreating links & editing fstab & reinstalling software was all the same. So with an install, I tried to do as much as I could from command line, listed my history and copied history commands into a bash  file. 

First few times I had to go back to old install to find something I missed, but now that is very rare.
       Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

---

### Post by mikodo on 2015-08-17
Thank you, Fred. I heard the warning!

After looking at all the info you present here, I know I will have take to my time with it, later.

But, thanks for showing what to move towards.

Seems all I've done lately is struggle with this install. Once I am back and running, I'm taking a break, and will spend free time doing something else.

I've saved your advice, and will pick away at following it later.

Again, thanks for making the effort, to show me a better way.

Kind regards!

---

### Post by sudodus on 2015-08-17
As always, *oldfred's* advice is good. I can only '+1' for it.

I also want to add replies to your questions:

> **mikodo said:**
> ...
I want to put in a larger second drive in the computer, and use dd to image the original drive to the newer/larger second drive. Then, destroy the original drive.

I will use this, as outlined here by TheFu in post #2, to image the whole present drive as a guide:  [http://ubuntuforums.org/showthread.php?t=1929671](http://ubuntuforums.org/showthread.php?t=1929671)

Questions.

 Can I leave the symbolic links, to the fstab mounted /mnt/data partition and expect the symbolic "data" links to work, like on the replaced drive?

Yes, if the cloning is successful it includes also symbolic links. But of course, the data partition should be connected (when you boot into the cloned system) if it is mounted via fstab, otherwise the booting will not finish.
> 
Would I need to format the new disk similarly, as Ext4 file system like the original  drive, before using dd or, will dd do that too?

No, do not format. dd will overwrite it anyway.
> 
If not, I am going to a fresh install on it, and start over. (data is backed up on two usb nodes).

I will not use Partimage, Partclone, Clonezilla, FSArchiver or, the likes. Maybe later,  when I have more time, I might investigate these.

Thank you.

I use Clonezilla for cloning and making 'full' backups. It is safer, because there are questions that let's you think and check twice, and also faster, because it does not copy free space (unused data blocks).

But it is often a good idea to make a fresh install instead, as *oldfred* suggests.

---

### Post by mikodo on 2015-08-17
Hi, sudodus.

Thank you, for the advice and explanations.

From what you shared, Clonezilla does sound like a good app/utility.  dd was appealing, as I was looking to do a  quick command with it, and go for coffee ... lazy. Not really ... tired.

Your advice, is taken under advisement, too.

Have a nice day!

---

### Post by sudodus on 2015-08-17
You marked this thread as SOLVED. Does it mean that cloning with dd was successful? Or only that there are replies to your questions? Anyway, when your computer is running from the new drive, please share your solution :-)

---

### Post by mikodo on 2015-08-17
> **sudodus said:**
> You marked this thread as SOLVED. Does it mean that cloning with dd was successful? Or only that there are replies to your questions? Anyway, when your computer is running from the new drive, please share your solution
Hi, sudodus!

You had answered my questions. That solved it for me ...

I'm leaning towards reinstall, when the new drive is available. I went to bed thinking that way anyway. It would also be fun to run the dd and go to bed, and in the morning disconnect/remove the old drive and reboot again, to see the state of things. There shouldn't be any harm or foul in that, as my data would still be intact and if needed, I could reinstall over the failed dd clone.

On the other hand ... as I said earlier, it would be a good exercise for me to do the new install bringing my data back from backups now. I'm going to do that. If, perchance, I change my mind and go the dd route, I will enter a response here, per your request, to share the results.

I have your responses for later, if/when I want to play with imaging with dd or Clonezilla and the like.

Kind Regards!

---

### Post by mikodo on 2015-08-20
Well folks, perchance has happened. I am going to try to image my new drive with dd.

I spent the last while moving my data partition to other partitions and moving those to other partitions. I am pretty confident with that now. Same for the symbolic link procedures. All well documented. Plus, my data is backed up from here to Sunday now, on 3 usb nodes.

The tech guy where I picked up my order from, put my new  identical hard-drive in my desktop box. Now, I have the working one and the new one.

They are switched in the housing so, I can easily pull the power cable to the old drive (it's in front), if I wish. If dd fails well, I'm confident now, I can reinstall everything fine.

See the Ubuntu pastebin below of  sudo lshw -C disk  and  sudo fdisk -l

The new disk is seen with no data on it as:

*-disk:0  is  Disk /dev/sda    500.1 GB, 500107862016 bytes

The old disk with Xubuntu 14.04 OS and my data partition is seen as:

*-disk:1    Disk /dev/sdb    500.1 GB, 500107862016 bytes

I plan to run in a live cd environment tonight, before going to bed:
> sudo dd if=/dev/sdb of=/dev/sda

Will I have to choose in the BIOS, which disk I want to boot into in the morning? (I've never had two internal disks in my computer before).

[http://paste.ubuntu.com/12138680/](http://paste.ubuntu.com/12138680/)

Thank you.

---

### Post by VMC on 2015-08-20
One problem you will encounter is by using 'dd' both hd's will have the same uuid. Unless you have one of them unplugged at time of boot.

edit: as sudodus suggested, Clonezilla is the best. You taking the long way home by using 'dd'. It copies all sectors, even empty ones. Clonezilla copies only used sectors and will verify image after backup.

---

### Post by mikodo on 2015-08-20
> **VMC said:**
> One problem you will encounter is by using 'dd' both hd's will have the same uuid. Unless you have one of them unplugged at time of boot.... Hi, VMC!

Thank you, for the advice.

Maybe, I'll look more into Clonezilla.

Does have its' supporters.

:)

---

### Post by oldfred on 2015-08-20
If you use dd, do not reboot with both drives connected. 

As VMC points out you have duplicate UUIDs. And it may then find one drive for one partition and the other drive for other partitions and drives get out of sync and you cannot then copy one to the other to fix.

Either immediately disconnect other drive, or go into old drive and change all UUIDs. If gpt much more difficult as it is both UUID & GUIDs.

---

### Post by monkeybrain20122 on 2015-08-21
I have been using fsarchiver to move installations around hard drives. e.g I moved Ubuntu 15.04 from an external hard drive to my internal and moved 14.04 to the external now that I have switched to 15.04 but still keeping 14.04 as a backup install (in case I don't like 15.10 and 15.04 goes eof I can switch back) It is pretty fast and seems safer than dd. And it can do it live so you can do the cloning while still using the computer.

You can change the uuid by booting from a live usb, then attach the drive you want to change uuid and use gparted. After that edit fstab and grub.cfg (of the one installation you just chaned uuid, not the one you are in currently) to change to new uuid, or the install will not boot (but as oldfred said with gpt it is more complicated. So I am not sold on its so called advantages ;))

[http://ubuntuforums.org/showthread.php?t=2221842](http://ubuntuforums.org/showthread.php?t=2221842)

---

### Post by mikodo on 2015-08-21
Thanks folks, for the information.

On FSArchiver. I remember it vaguely from when I looked into it, while it was Alpha/Beta. 

It does sound good, that one could do the cloning while the computer is on so, searching for help tutorials, would be readily available.

I am going to read more tomorrow and then decide what to do.

What I had like about dd is, I would just have to run a command and forget about reading any thing else. :)

Bye for now ...

---

### Post by mikodo on 2015-08-22
Hi everyone.

I wish to thank everyone for their thoughtful replies in this thread.

I read Clonezilla guides and settled on using it initially, as it was suggested by multiple posters. (I don't have a lot of time to read a lot of tutorials on other imaging utilities). 

When I came to using Clonezilla  yesterday, I couldn't use it with the way the two drives were mounted physically in the computer. The cabling was reversed and I couldn't put the image on the blank drive.

That gave me pause, to think.

I could continue with Clonezilla by switching the cabling for the internal drives, or use a usb node for the image initially, or  run the dd commands, or take out the old drive and practice with bringing back my data from a backup and setting up another data partition in /mnt/data/ and symbolically linking it to ~/ in a new install.

I chose the latter and took out the old drive and reinstalled the Xubuntu OS to the new one. I have successfully returned the backup data to a  /mnt/data/ partition that is symlinking to ~/.

I learned lots in these exercises. I may want to image with Clonezilla in the future. It does look good and I have a beginners feel for it now.

I am especially happy, I went through the exercise of reinstalling and bringing my data back to a symbolically linked /mnt/data/ partition, and I am just finishing my succinct documentation to save for my readily upcoming old age. lol.

Thank you all, for your advice. 

I am going to put this thread to sleep with solving it, even though I didn't follow through with imaging now. I have the answers to my questions from you folks, and my experience with dabbling with Clonezilla.

Bye for now ...

---

### Post by sudodus on 2015-08-22
I'm glad Clonezilla worked for you, and thanks for sharing your solution :-)

---

