---
title: "Crashed /etc..NEED HELP PLEAS!!!???"
date: 2008-03-15
forum: General Help
---

### Post by CD27 on 2008-03-15
Ive been doing some searching for a while, and haven't found anything. Contacted one person for some help, and he told me to use fdisk -l. Well, it would help, but the only drive that shows up is my external hard drive. I'm trying to access my original linux hard drive via the live cd, but once I unplugged the external hard drive when i run fdisk -l nothing comes up....NOTHING. If you want to find out WHY i am doing this, go to this thread: [http://ubuntuforums.org/showthread.php?t=724819](http://ubuntuforums.org/showthread.php?t=724819)

I Desprately need to find out how to get to my drive. I can't afford to reinstall, i have WAY TOO MUCH important stuff on that drive that will take me a couple of dozen hours to reinstall later if i wipe the hard drive. Any help, PLEASE!?

---

### Post by CD27 on 2008-03-15
Anyone? Hello?

---

### Post by Iandefor on 2008-03-15
Have you tried opening up the partition editor (System->Administration->Partition editor)? It should detect and display the block device of your hard drive/partition.

Then just mount it normally (ie, "mkdir /mnt/foo && mount [device] /mnt/foo") and you should be able to access it.

---

### Post by CD27 on 2008-03-15
Okay, so i found it, but it keeps telling me this:

ubuntu@ubuntu:~$ mkdir /mnt/foo && mount /dev/hda2 /mnt/foo
mkdir: cannot create directory `/mnt/foo': Permission denied
ubuntu@ubuntu:~$ mkdir /mnt/foo && mount /dev/hda1 /mnt/foo
mkdir: cannot create directory `/mnt/foo': Permission denied
ubuntu@ubuntu:~$ mkdir /mnt/foo && mount /dev/hda1
mkdir: cannot create directory `/mnt/foo': Permission denied
ubuntu@ubuntu:~$ mkdir /mnt/foo && mount /dev/hda /mnt/foo
mkdir: cannot create directory `/mnt/foo': Permission denied
ubuntu@ubuntu:~$

---

### Post by CD27 on 2008-03-15
anyone else maybe?

---

### Post by CD27 on 2008-03-15
Don't know about you guys, but it's like 3:00 in the freaking morning over here, would really like an answer now...MAYBE an answer, kinda?

---

### Post by Mustard on 2008-03-15
Wouldnt you need to use the 'sudo' command in front of the mkdir command to execute the command as root?

---

### Post by CD27 on 2008-03-15
now it just says:

ubuntu@ubuntu:~$ sudo mkdir /mnt/foo && mount /dev/hda /mnt/foo
mkdir: cannot create directory `/mnt/foo': File exists
ubuntu@ubuntu:~$ 

:|

---

### Post by Iandefor on 2008-03-15
mkdir is failing because /mnt/foo already exists (so it can't create it).

just do ```
mount [device] /mnt/foo
``` now.

---

### Post by danwood76 on 2008-03-15
You wont be able to mount the entire disk, you can only mount partitions.
could you post the output of:
```

sudo fdisk -l

```

the reason why you couldnt see your drive originally is because you need to use sudo (have root privaliges) to see all the devices.

---

### Post by CD27 on 2008-03-15
lol, obviously I'm a complete noob at this.....it gave me this, which i thik is a bit easier to figure out, but i'm still having trouble finding info on it:

ubuntu@ubuntu:~$ sudo mount /dev/hda /mnt/foo
mount: you must specify the filesystem type
ubuntu@ubuntu:~$

---

### Post by CD27 on 2008-03-15
here it is:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4700    37752718+  83  Linux
/dev/hda2            4701        4864     1317330    5  Extended
/dev/hda5            4701        4864     1317298+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by danwood76 on 2008-03-15
The error you got was because of what I said earlier, you are trying to mount the disk not the partition.
This will work for you tho:
```

sudo mount -t ext3 /dev/hda1 /mnt/foo

```

---

### Post by CD27 on 2008-03-15
it went through, but i still don't see the mounted drive

---

### Post by danwood76 on 2008-03-15
you wont see it if its mounted in /mnt but you can browse to it by first going to the filesystem then the mnt folder.

if you were to have mounted it in /media it would appear on the desktop.

So you could do that by doing:
```

sudo umount /mnt/foo
sudo mkdir /media/foo
sudo mount -t ext3 /dev/hda1 /media/foo

```

---

### Post by CD27 on 2008-03-15
wow, i learn something new every day! that worked. Okay, so now what I'm trying to do is copy the /etc dir from the livecd OVER the /etc on the mounted drive. unfortunately, i don't have permissions to do anything to the one on the mounted drive. do you know the command i need to type to remove the /etc on the mounted drive and replace it with the /etc on the livecd?

---

### Post by danwood76 on 2008-03-15
what you can do is run the file manager as the super user so
```

sudo nautilus

```

just note that you wont be able to drag and drop stuff in or out of this window as you wont have the su privalages outside of it.

---

### Post by CD27 on 2008-03-15
Whew, alrighty then. I think I screwd up again, and you're probably gonna hate me for this....wow (note to self....ATTENTION TO DETAIL SHIPMATE!) I was an idiot and forgot to backup /etc/passwd and /etc/groups. When i rebooted my computer after copying successfully over the entire /etc of the mounted hard drive with the livecd's /etc, it wouldn't go into the login menu, instead gave me a few things that had to do with /etc and permissions, something, i didn't write them down cuz it was too long.

---

### Post by danwood76 on 2008-03-15
What I would do is backup your needed data and re install.
After reading the other thread I would have just done this in the first place.

Just remember not to mess around with permissions again :)

---

### Post by CD27 on 2008-03-15
i can't afford to do that, I've got WAY too much data and literally hundreds of applications that took me hours to install and update. if i didn't have the ties to it, i certainly would have reinstalled

---

### Post by CD27 on 2008-03-15
.....*sigh*.....okay, what do I have to do to ensure that when I reinstall all of the software I have on it right now will be reinstalled, and all of my files are backed up (including upgrading my ubuntu version)

---

### Post by CD27 on 2008-03-15
?

---

### Post by danwood76 on 2008-03-15
can you log into your system in recovery mode?

if you can then you can save the software list and restore it when you reinstall.
I would download the gutsy install CD from the net and not install fiesty and upgrade (you will probably have to download the same amount either way)

heres a guide to saving the software list and restoring it:
-- deleted --
follow the debian based instructions

-- edit --

that guide is a little incomplete, im gonna search for a better one

this guide is better:[http://ubuntu-tutorials.com/2006/12/05/how-to-clone-an-installation-ubuntu-510-6061-610/](http://ubuntu-tutorials.com/2006/12/05/how-to-clone-an-installation-ubuntu-510-6061-610/) ot will work with gutsy.

---

### Post by danwood76 on 2008-03-15
You will also need to copy all your files to an external drive.
Normally all your stuff will be stored in your home folder *** you dont have permissions anywhere else but it depends on things youve done.

---

### Post by CD27 on 2008-03-15
no, i can't boot into safe mode (recovery mode), i won't boot anything except the cd correctly. I also don't have a burner on my computer, so I'll have to stick with the version of linux I have now. Thanks for your help, you've really got me a far way, and I've learned a great deal


Edit: Are you sure there really is no way I could simply restore, or put in a temporary, etc/password and etc/groups files so that I can at least just log in? I got this far, I'm sure that there's something I could do in order to get this entire issue solved. That's my main goal. It's not only because i don't want to have to go through the trouble of haveing to reinstall all my stuff, but also because I want to know that I was able to solve this problem. I know it's possible, I just can't find it.

---

### Post by hyperair on 2008-03-15
Do what I mentioned to you in the other thread. Just boot into a LiveCD, get the volume mounted and start fixing your permissions there. If you wish, you can just fix the permissions in /etc/passwd and /etc/groups as well as /etc/shadow first before going back to your broken installation and fixing the rest. However, I honestly think this complicates matters a little further than necessary.

To get your hard disk mounted in a LiveCD, just open all disk drives listed under Places->Computer. The one that has a similar directory structure to / should be the appropriate one.

---

### Post by CD27 on 2008-03-15
whenever I try to regular boot, this is what I get:

udved:[2497]: add_to_rules:PHYSDEV* values are deprecated and will be removed from a future kernel, please fix it in /etc/vdev/rules.d/40-permissions.rules:17
udved:[2497]: add_to_rules:PHYSDEV* values are deprecated and will be removed from a future kernel, please fix it in /etc/vdev/rules.d/40-permissions.rules:45
udved:[2497] lookup_group:specified group 'nvram' unknown
Udved:[2497]: add_to_rules: do not reference parent sysfs directories directly, that may break with a future kernel, please fix it in /etc/vdev/rules.d/65-persistent-storage.rules:12


I forget if those are "udevd" or "udved".

---

### Post by CD27 on 2008-03-16
Okay, I went to bed around 7:30 in the morning, it's about 1:00 in the afternoon now, so i;m back up. No one knows what this is?

---

### Post by hyperair on 2008-03-16
Probably the same permissions error as when you messed up your entire /etc folder. You know what, I think you should copy the permissions from the LiveCD /etc, and set the /etc on your system accordingly. All in a LiveCD. That should fix any problems you're having. Hwoever, it might take some time to complete.

---

### Post by CD27 on 2008-03-16
well, I have alread completely written over the /etc folder, that's why those errors came up, but i don't know how to change the permissions to begin with, no one really answered that question for me.

---

### Post by hyperair on 2008-03-16
Mann I pity your computer. I say give it a quick reinstall after backing up your /home directory.

---

### Post by CD27 on 2008-03-16
why, what's wrong? what did you see? Is it really so screwed up that I can't just type a few commands into terminal and fix the entire thing from there? I assume that's the issue, and noone knows the freaking commands.

---

### Post by Iandefor on 2008-03-16
> **CD27 said:**
> whenever I try to regular boot, this is what I get:

udved:[2497]: add_to_rules:PHYSDEV* values are deprecated and will be removed from a future kernel, please fix it in /etc/vdev/rules.d/40-permissions.rules:17
udved:[2497]: add_to_rules:PHYSDEV* values are deprecated and will be removed from a future kernel, please fix it in /etc/vdev/rules.d/40-permissions.rules:45
udved:[2497] lookup_group:specified group 'nvram' unknown
Udved:[2497]: add_to_rules: do not reference parent sysfs directories directly, that may break with a future kernel, please fix it in /etc/vdev/rules.d/65-persistent-storage.rules:12


I forget if those are "udevd" or "udved".Can you chroot into the filesystem? Try:```
sudo chroot /media/hda1
``` That should give you a root shell on it without needing to reboot into it. The problem with the nvram group should be fixable with:```
groupadd -g 105 nvram
``` from the chroot environment.

---

### Post by CD27 on 2008-03-16
it gives this: (note, I am working on a live cd, i haven't remounted the drive yet, would that cause this failure?)

ubuntu@ubuntu:~$ sudo chroot /media/hda1
chroot: cannot change root directory to /media/hda1: No such file or directory
ubuntu@ubuntu:~$ sudo groupadd -g 105 nvram
groupadd: GID 105 is not unique
ubuntu@ubuntu:~$ groupadd -g 105 nvram
groupadd: unable to lock group file
ubuntu@ubuntu:~$

---

### Post by Iandefor on 2008-03-16
Sorry, I thought /media/hda1 was still mounted. Try mounting it first (remembering, of course, to have created the directory /media/hda1 first!)

---

### Post by CD27 on 2008-03-16
okay, so i remounted it, and this is what came out:

ubuntu@ubuntu:~$ sudo chroot /media/foo
root@ubuntu:/# groupadd -g 105 nvram
groupadd: GID 105 is not unique
root@ubuntu:/#

---

### Post by CD27 on 2008-03-16
lol, trust me when i say that when this problem has been solved i will make a step by step guide of how to fix it for any other idiot that messes with overall permissions on the /etc directory...sheesh! lol .....If this was a windows issue I would have solved it in the first hour of working on it..good gracious!

---

### Post by CD27 on 2008-03-16
anyone else have any ideas?

---

### Post by Iandefor on 2008-03-16
the only one that jumps to mind is ```
groupadd nvram
``` in the chroot. I guessed 105 would work after looking at my /etc/groups file, though apparently not.
> lol, trust me when i say that when this problem has been solved i will make a step by step guide of how to fix it for any other idiot that messes with overall permissions on the /etc directory...sheesh! lol .....If this was a windows issue I would have solved it in the first hour of working on it..good gracious!    	It truly* is* a horrid pain to remove /etc/group and /etc/passwd. Basically all your user information goes out the window with those two, and since your interactions with the computer are as a user... well, obviously it's not going to be pretty. I don't think I've seen a problem so severe with a Linux box before, and believe me, I've seen some severe problems.

---

### Post by CD27 on 2008-03-16
well, I ran that command, "sudo groupadd nvram" and it went through, what do you think I can do now?

yeah...all this from the freaking hosts.txt file..WOW

U know, I think i could have gotten this problem fixed last night if i didn't have to rely on doing intense useless searches and rely on someone else to post back when if i had someone professional to talk to via yahoo, MSN, or AOL messengers i'd be absolutely fine right now i think.

---

### Post by Mustard on 2008-03-16
> **CD27 said:**
> well, I ran that command, "sudo groupadd nvram" and it went through, what do you think I can do now?

yeah...all this from the freaking hosts.txt file..WOW

U know, I think i could have gotten this problem fixed last night if i didn't have to rely on doing intense useless searches and rely on someone else to post back when if i had someone professional to talk to via yahoo, MSN, or AOL messengers i'd be absolutely fine right now i think.

You should hire someone then. :)

---

### Post by CD27 on 2008-03-16
well, i found someone online who had messenger and the problem is almost fixed now :D

---

### Post by Sef on 2008-03-16
Locked. Duplicate Thread.  See Post 1 for other thread.

---

