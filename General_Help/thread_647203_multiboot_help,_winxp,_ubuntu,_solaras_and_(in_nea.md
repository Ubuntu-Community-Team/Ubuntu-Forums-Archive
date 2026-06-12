---
title: "multiboot help, winxp, ubuntu, solaras and (in near future) debian"
date: 2007-12-22
forum: General Help
---

### Post by big dizzle on 2007-12-22
Sry for kind of long post but...

I installed ubuntu about a week ago, after installing winxp.  Last night I installed solaris 10, and now at my boot menu, I only see xp and solaris, no ubuntu :(

I installed all three on my master hard drive (xp on first partition, ubuntu 7.10 on the second, a swap partition for ubuntu on the third, and solaris 10 on the fourth).  SIDENOTE: After I've figured this out I plan to install debian on another partition.

My guess is this happenned b/c solaris installed a diff version of grub (at the boot menu it says the grub version is 0.95).  I've tried to google this problem, and I've found examples on configuring grub (which I think I understand b/c I've taken some classes on programming in both c++ and java and even though I know its not the same I kind of get it)...anyway these examples I find show code for configuring grub, but don't show me how to enter grub command line to make these changes.
So here are my questions:

1) How do I get into grub to make changes, and given how I have my hard drive set up, what code should I use/change in order to have all three operating systems show up on the boot menu?  If I should install a diff version of grub and start from scratch, that would be cool but plz give me explicit instructions on how/where to do so.

2) Is this just going to happen again when I reinstall Debian?  Should I install debian first, and then go through the trouble of configuring grub?

Still reading? ok good.  Like I said earlier, sry for the long post and any help is appreciated :)

---

### Post by big dizzle on 2007-12-22
correction, i won't be installing debian, i will be installing it for the first time:KS

---

### Post by nick_h on 2007-12-22
To get into grub type:
```
sudo grub
```
Then to find out which partitions have grub on them - from the grub prompt type:
```
find /boot/grub/stage1
```
This will list locations in a format like:
(hd*drive*, *partition*)
where both number from 0 - see section 2 of the [Grub manual](http://www.gnu.org/software/grub/manual/grub.html).
To install (section 3 in the manual) you just have to set the root device and tell it where to install.  If you want to use the grub in partition 2 and install it to the MBR of the first disk then type:
```
root (hd0,1)
setup (hd0)
quit
```
The configuration files are in /boot/grub/menu.lst
I suggest a cut and paste of the relevant lines.
If you install another OS it may reinstall grub but then simply repeat the above steps.

---

### Post by big dizzle on 2007-12-23
thnx for the reply!  i just need you to clarify one thing for me, where do i type in the "sudo grub" command?

---

### Post by big dizzle on 2007-12-23
So from the grub command line I typed:

```
find /boot/grub/stage1
```

and I got the following (verbatim):

> 
  (hd0,2,a)
  (hd0,4)


Now, this confuses me a little, because the grub manual says that the partitions are numbered from 0, not from 1.  So by that logic my 0 or first partition should be win xp, my 1 or second partition should be ubuntu, my ubuntu swap partition should be 2, and my solaris partition should be 3.  But for whatever reason, it isn't.  

I'm guessing that the two partitions which are listed are my ubuntu and solaris partitions, respectively.  So I tried two things, first I followed your code exactly:

```
root (hd0,1)
```

and this gave me the following:

>   Filesystem type unknown, partition type 0xf

Then I tried the following command, based on the list that the find /boot/grub/stage1 command gave me:

```
root (hd0,2,a)
```

and that gave me the following:

>   Filesystem type is ufs, partition type 0xbf

Assuming this was ok, I tried the next command you gave me
( setup (hd0) ) and was given this:

> Error 6: Mismatched or corrupt version of stage1/stage2

Also, quit wasn't on the command list (the list given when I press tab).

What am I doing wrong?

---

### Post by Craigus on 2007-12-23
Try SuperGRUB, it can probably sort it all out for you:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by MetalheadGautham on 2007-12-23
If you install debian in the end, and use it to detect other installed OSes, I am sure you will be able to Access Ubuntu again. Though the question why anyone may want both ubuntu AND Debian is something that I keep getting in my mind. You are better off trying the Fedora 8 for now, if you want some change. Its logo also has something that looks like the number 8 in it, and its the first to have PulseAudio. So its a landmark release and recomended for install.

---

### Post by nick_h on 2007-12-23
> What am I doing wrong?
It looks like you have Ubuntu in an extended partition (4) and Solaris in primary partition (2).
If you post the output from:
```
sudo fdisk -l
```
then it will show how you have partitioned the disk.

---

### Post by big dizzle on 2007-12-23
When I try the sudo command, I get a message saying that it isn't a valid command.  I hit tab to list the commands and it isn't there.  Maybe I'm trying the commands from the wrong place?  When my boot menu shows up, I press "c" to enter the command line, and it brings me to a command prompt that looks like this:

> grub>

Am I not in the right place?

Also, in response to Metalhead's post, I was thinking the same thing about just installing the next operating system ( I'm thinking Debian, but might go Redhat now.  I'm just new to anything outside of windows, so I'm looking to try out a broad field of oses).  I think that this could work b/c I double checked my partitions (to make sure I didn't do something stupid like overwrite my ubuntu partition when I installed solaris) and the partition is still there.

Either way I will post whatever I end up doing that works :)

---

### Post by nick_h on 2007-12-23
Run the "sudo fdisk -l" from a terminal (not within grub) - it will confirm what partitions you have.

Installing Debian and re-installing grub may well also fix your problem.

---

### Post by big dizzle on 2008-01-08
Ok, I didn't fix my problem, but I found out a way to make it work how I want it to when I reinstaled the OSes.  So if you ever want to set up a system w/more than two operating systems, this is how I would recommend doing it.  btw, this assumes you are installing windows, and then various oses which use GRUB

1 - Install windows on a partition
2 - Install your next OS on another partition
3 - Once your next OS is installed, go to the boot folder, then the grub folder, and then open the menu.lst file.  Copy the part of the file that puts your OS onto the GRUB menu which looks something like:

> title YourOSName
root (hdx, x)
kernel blablabla
module blablabla

Paste this into a text file, or something that is compatible across various OSes.

4 - Install your next Operating system and do the same as step 3.
5 - Once you have installed your last operating system go to the boot folder, then the GRUB folder, then open the menu.lst file.  Paste all of the things that you copied to the end of the file.  This will change your GRUB menu to include all of the operating systems you have installed.

I'm sure there is probably a million other ways to do this, and given how much experience I have I doubt that this is anywhere near the best.  But it is how I got my computer to do what I wanted it to do.

Thnx all for all your help!

---

