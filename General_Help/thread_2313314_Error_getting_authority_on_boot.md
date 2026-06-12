---
title: "Error getting authority on boot"
date: 2016-02-11
forum: General Help
---

### Post by &amp;*@Fth&amp;% on 2016-02-11
This happened after a kernel update. Whenever I try to boot, my computer says "Error getting authority: Error initializing authority: Could not connect: No such file or directory (g-io-error-quark, 1) Welcome to emergency mode!..." followed by abunch of things I can do. It spits the same error out if I ctrl-d to boot into default mode, and the fstab file matches the drive UUIDs perfectly. I seem to be able to boot up normally if I select emergency mode from the GRUB menu, and do something that mounts the file system (like "clean"). It still spits out the error, but I can select resume booting and it works fine.

---

### Post by ajgreeny on 2016-02-11
Can you boot using an earlier kernel from the grub menu?

---

### Post by &amp;*@Fth&amp;% on 2016-02-11
It does the same thing. Which is quite wierd, now that I think about it. But that's what happens.

---

### Post by QDR06VV9 on 2016-02-11
This usually means one of your mount points is failing. View the log to see which one.
```
journalctl -xb
```
Search the log for the word mount

---

### Post by &amp;*@Fth&amp;% on 2016-02-11
Some of the results:
Failed to insert module kdbus: function not implemented 
Warning: mounting fs with ereoes, running e2fsck is recommended

The other results seemed inconsequential.

---

### Post by QDR06VV9 on 2016-02-11
Here is all i can find
[http://comments.gmane.org/gmane.linux.ubuntu.devel.kubuntu/10182](http://comments.gmane.org/gmane.linux.ubuntu.devel.kubuntu/10182)
And
[http://osdir.com/ml/ubuntu-bugs/2015-07/msg17633.html](http://osdir.com/ml/ubuntu-bugs/2015-07/msg17633.html)
I have heard this put

> Unfortunately some bad decisions were made with systemd including a lack of fault tolerance and a lack of actionable error messages. It's not at all clear that the advantages of systemd outweigh the disadvantages
Sorry I can not be more helpful.

---

### Post by &amp;*@Fth&amp;% on 2016-02-11
So you're basically saying that I'm screwed here? That can't be right though, because other people aren't having this problem.

---

### Post by QDR06VV9 on 2016-02-12
> **superrobowizard said:**
> So you're basically saying that I'm screwed here? That can't be right though, because other people aren't having this problem.

Those are your words not mine, with the information you have supplied not a lot to go on here. Which makes it very hard to help!
Warning: mounting fs with ereoes, running e2fsck is recommended

That's a warning, not an error, and a recommendation, not a command.

The warning: mounting fs with errors, running e2fsck is recommended is a bit more worrying but can probably be fixed by e2fsck.

This all comes down to /etc/fstab options. A typical fstab partition entry looks like this:
> # <file system>       <dir>         <type>    <options>             <dump> <pass>
UUID=123-456-ABC-DEF   /             ext4      defaults,noatime      0      1

The last field, pass, specifies how/when the disk should be checked for errors. If it is set to 0, the drive will never be checked, if set to 1, it will be checked on each boot and if set to 2 or more, it will be checked each time it has been mounted more than a specified (30 by default) number of times without being checked.

Given the warnings you observe, my guess is that yours is set to 0 in your /etc/fstab. The recommended values are 1 for your /partition and 2 or higher for everything else. If set at a value greater than 1, the system will check your drive for errors every 30 mounts.
But first check the < /etc/fstab > first and make sure the values are not set to "0" without the quotes
If needed: [http://askubuntu.com/questions/353732/how-to-use-fsck-in-ubuntu](http://askubuntu.com/questions/353732/how-to-use-fsck-in-ubuntu)

---

### Post by &amp;*@Fth&amp;% on 2016-02-12
I attached my fstab file (it didn't have the .txt, I had to add that so it would let me upload the file). The numbers look fine to me according to what you said, but I don't want to go tweaking things and break it. You can take a look at it and see if anything looks off to you (this stuff is way over my head).

---

### Post by QDR06VV9 on 2016-02-13
So you did not change anything yourself? Is this Right?
Post back the generated text from this in the terminal:
```
dmesg | grep mount
```
The more info we can get is the best in making the correct modification's;)
If you don't know how to to copy from the terminal, take your mouse and highlight the text in the terminal and then use the keyboard combo of <Ctrl> +<Shift> +<c>  or right click the highlighted text and choose "copy"
Then paste it to a text editor like Gedit or Pluma or Kate... you get the idea.

---

### Post by &amp;*@Fth&amp;% on 2016-02-13
Yep, didn't change anything.

Command output:
```
[    2.089414] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[    2.211520] systemd[1]: Set up automount Arbitrary Executable File Formats File System Automount Point.
[    6.002340] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[    6.008209] EXT4-fs (sda1): warning: mounting fs with errors, running e2fsck is recommended
[    6.009522] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[20447.900210] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[21180.584318] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[21192.608057] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
```

---

### Post by QDR06VV9 on 2016-02-15
Hey superrobowizard!
Sorry I almost forgot about you!;)
Any way I think we are safe to have boot-up to check disk errors
The command below will on the next boot run fsck to find and repair mounts.
```
sudo touch /forcefsck
```

Fsck will in theory fix errors on the next boot-up so be patience for the boot will take just a little longer. 

If you want to Make it check and reboot presently
```
sudo shutdown -r -F now
```
I would for the first time use the top or first command..
*****Now the warning** **this should cause no bad effects to your system but you should have a good back-up in place.
If you do not.. _Do it Now.  Things can go wrong._
When done run the "dmesg | grep mount" and the error should not show the "EXT4-fs (sda1): warning: mounting fs with errors, running e2fsck is recommended"

---

### Post by &amp;*@Fth&amp;% on 2016-02-15
That message isn't printed by your command, but it still puts me in emergency mode. At the top it says "no chaching mode found" "assuming drive cache: wrote through", and then the emergency mode message. Also I assume you meant shutdown now not shutdown no :)

---

### Post by QDR06VV9 on 2016-02-15
> **superrobowizard said:**
> That message isn't printed by your command, but it still puts me in emergency mode. At the top it says "no chaching mode found" "assuming drive cache: wrote through", and then the emergency mode message. Also I assume you meant shutdown now not shutdown no :)
So the warning: mounting fs with errors, running e2fsck is recommended is gone now, but we boot to emergency mode [B]still??
[/B]Could you please post that content from 
```
dmesg | grep mount
```

And also the content of this paste back
```
kate /etc/fstab
```

---

### Post by &amp;*@Fth&amp;% on 2016-02-15
Can't copy-paste as I have to do this from my phone (also having internet issues) but I'll try to type it out.

Just so you know I have the OS in one partition and my home folder in another. (OS is sda2, home is sda1)

```
Dmesg | grep mount:
EXT4-fs (sda2): mounted file system with ordered data mode. Opts: (null)
systemd[1]: set up automount Arbitrary Executable File Formats File System Automount Point.
EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
```

If I boot properly using the recovery mode trickery, it says the same message but appends this:
```
EXT4-fs (sda1): warning, mounting fs with errors, running e2fsck is recommended (lol)
EXT4-fs (sda1): mounted file system with ordered data mode. Opts: (null)
```

---

### Post by QDR06VV9 on 2016-02-15
It's worth saying that any failed fstab mount will cause full system failure with meaningless error messages. Includes cd, dvd, swap, mapper and data partitions. 
Put the nofail option on to every line in /etc/fstab that you think might not be available at any boot time.(Hint)<sda1>
Mine looks like this
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
#
UUID=20bdf831-792b-42fb-9f0a-7c2cc6096a04 / ext4 defaults,rw,relatime,data=ordered 0 1
UUID=491d9d5b-ebaa-407c-bb15-bba80f556bf1 swap swap defaults 0 0
```
So where mine says "**ext4 defaults,rw,relatime,**"put , nofail," at the end of that string.
The commas are very important
I suspected the home partition was on a different partition..
Just to be sure you follow my text it should look something like this <**ext4 defaults,rw,relatime,**[COLOR=#ff0000]nofail, [/COLOR]data=ordered 0 1[COLOR=#ff0000] [/COLOR]

---

### Post by &amp;*@Fth&amp;% on 2016-02-15
That worked, but now all of my settings are gone!

---

### Post by &amp;*@Fth&amp;% on 2016-02-16
It seems that after adding the nofail thing it doesn't mount my home folder. I have to manually mount it, then log out and back in again.

---

### Post by QDR06VV9 on 2016-02-16
Still waiting for this COPY and Paste Here
```
kate /etc/fstab
```
**The whole content of the terminal out put...**

---

### Post by &amp;*@Fth&amp;% on 2016-02-16
Copy-pasted from post #9 w/ added nofail:

```
# /etc/fstab: static file system information.
# # Use 'blkid' to print the universally unique identifier for a # device; this may be used with UUID= as a more robust way to name devices  that works even if disks are added and removed. See fstab(5).
# # <file system> <mount point> <type> <options> <dump> <pass>
# / was on /dev/sda2 during installation
UUID=08fbf948-9860-4678-b9ac-6554e23af18e / ext4 nofail,errors=remount-ro 0 1
# /home was on /dev/sda1 during installation
UUID=84edc9b9-5b22-4ad6-a5e3-022cb1b3b619 /home ext4 nofail,defaults 0 2
```

---

### Post by &amp;*@Fth&amp;% on 2016-02-23
Problem still isn't solved. Bump.

---

### Post by QDR06VV9 on 2016-02-23
@superrobowizard
Try removing the "nofail" only from this line..
 **UUID=84edc9b9-5b22-4ad6-a5e3-022cb1b3b619 /home ext4 nofail,defaults 0 2**

So it should now look like this
**" UUID=84edc9b9-5b22-4ad6-a5e3-022cb1b3b619 /home ext4 defaults 0 2 "**
 Fingers Crossed

---

### Post by &amp;*@Fth&amp;% on 2016-02-23
Nope, that kicked me back into emergency mode. :(

---

### Post by oldfred on 2016-02-23
Did you run a full fsck from a live installer? Particularly on sda1, but on all ext4 partitions.
Example uses sdb1, change to your partition.

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by &amp;*@Fth&amp;% on 2016-03-11
Just tried that, encountered errors, fixed them, didn't help.

---

### Post by &amp;*@Fth&amp;% on 2016-03-20
Bump

---

### Post by oldfred on 2016-03-20
Post these:
sudo parted -l
sudo fdisk -lu
df -h
       sudo blkid -c /dev/null -o list

---

### Post by &amp;*@Fth&amp;% on 2016-03-20
sudo parted -l: [http://pastebin.com/gyXyxFd3](http://pastebin.com/gyXyxFd3)
sudo fdisk -lu: [http://pastebin.com/WzzCFFeU](http://pastebin.com/WzzCFFeU)
df -h: [http://pastebin.com/g0FbPhi7](http://pastebin.com/g0FbPhi7)
sudo blkid -c /dev/null -o list: [http://pastebin.com/tZ2hcZu8](http://pastebin.com/tZ2hcZu8)

---

### Post by &amp;*@Fth&amp;% on 2016-03-24
Bump

---

### Post by oldfred on 2016-03-25
Is sdb an external drive?

---

### Post by &amp;*@Fth&amp;% on 2016-03-25
No, it's internal. sda is a 500GB Eluktronics SSD, and sdb is a 500GB Samsung HDD.

---

### Post by oldfred on 2016-03-25
Did you run the fsck on all your ext4 partitions?

Is this still the issue?
```
 [    6.009522] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[20447.900210] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null) 


```

What I do not know for sure is if sda1 issue is timestamp for second entry or issue is sdb1 and its time stamp?
But huge delay for something.

This is my fstab where sda is SSD and data partition on sdb is HDD.
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=5c1e1a3f-261f-4da5-a0c2-8f479b3039de /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=D966-440A  /boot/efi       vfat    defaults      0       1
# swap was on /dev/sdb7 during installation
UUID=3ef43e7c-8a35-4f8b-bc73-c91d6098d4cd none            swap    sw              0       0
# Entry for /dev/sdb4 :
UUID=f9537995-8b44-4abb-b5fb-ec27023f57b2 /mnt/data ext4 relatime 0 2
# Reduce SSD wear
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
```

It looks like I forget to add the noatime on / , so I will be changing that.

---

### Post by &amp;*@Fth&amp;% on 2016-03-25
Yep, I ran it on all partitions. It said it found errors, and fixed them, but the problem was still the same.
To boot up I have to:
-select recovery mode from GRUB
-chose an option that mounts the file system (ex. 'clean')
-resume booting
-it kicks me into emergency mode
-mount the partition for /home
-ctrl-D
-the recovery mode prompt comes up again, press resume
-I get the login prompt, and everything works fine from there

/etc/fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=08fbf948-9860-4678-b9ac-6554e23af18e /               ext4    nofail,errors=remount-ro 0       1
# /home was on /dev/sda1 during installation
UUID=84edc9b9-5b22-4ad6-a5e3-022cb1b3b619 /home           ext4    nofial,defaults        0       2
```

---

### Post by QDR06VV9 on 2016-03-25
Just to point to a type-o
From your last post this
> # /home was on /dev/sda1 during installation
UUID=84edc9b9-5b22-4ad6-a5e3-022cb1b3b619 /home           ext4    [COLOR=#ff0000]nofial[/COLOR],defaults        0       2That should Read **"nofail"**

But wait for oldfred..

---

### Post by &amp;*@Fth&amp;% on 2016-03-25
Hehe... It works now. Sort of.

So I fixed my little (or maybe not so little) typo, and now I can boot normally.
But that still doesn't explain 2 things:
1 - why I am getting errors at all
2 - I don't get the startup splash screen, just a blinking _ in the top-left corner

---

### Post by oldfred on 2016-03-25
Always after editing fstab, run mount -a.
 # Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to, Make sure you have partition unmounted if previously mounted when creating new mounts:
sudo mount -a 

I would suggest standard parameters, as I posted above.

Root on SSD would be: noatime,errors=remount-ro
I use relatime for data partitions: relatime

---

### Post by &amp;*@Fth&amp;% on 2016-03-25
Well, I guess I just got lucky that it didn't completely screw up everything. I did sudo mount -a and it said nothing, so I assume everything was fine.

---

### Post by &amp;*@Fth&amp;% on 2016-03-25
Just rebooted, same problem

---

### Post by oldfred on 2016-03-25
Which error.

I get flashing underscore for just a bit, but with SSD now, it is not long.

If you want to see boot process, you can on grub menu remove quiet splash on linux line. Or edit 
  /etc/default/grub  to make permanent.

      
 At grub menu you can use e for edit, scroll to linux line and remove quiet splash.

---

### Post by &amp;*@Fth&amp;% on 2016-03-26
By the error I mean the error that is suppressed by nofail.
I'm looking for the Kubuntu logo to appear in the middle of the screen with the 4 little dots under it that fill up based on how far it is into the boot.

---

### Post by oldfred on 2016-03-26
The dots just say it is loading.
If you remove quiet splash you can actually see each drive loading & configuring. New systems with SSD, often scroll so fast it is hard to follow.

---

### Post by &amp;*@Fth&amp;% on 2016-03-26
Yes, but I want it to look nice. I have to reboot a lot, so I see that a lot. I spend a good amount of effort making everything look nice with things like GRUB themes. I looked, and the boot entry does have quiet splash. The quiet seems to be working (I assume that's what makes it show just the _ and not a bunch of text as it boots) but the splash part doesn't.

---

### Post by oldfred on 2016-03-26
That could be something in the theme settings then.
I never mess with that, I just want it to boot and quickly.
With SSD, now I barely see anything at all.

---

### Post by &amp;*@Fth&amp;% on 2016-03-26
I can't find it in settings. I suspect it may be broken, but I may be wrong. I can't find anything on it from Google-ing.

---

### Post by oldfred on 2016-03-26
Is this what you used for reference?

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

---

### Post by &amp;*@Fth&amp;% on 2016-03-26
Actually I just got a theme called 'Grau' from kde-look.org and modified it a bit.

---

### Post by &amp;*@Fth&amp;% on 2016-03-29
In addition to the underscore at startup, the screen will sometimes briefly flash as if the monitor momentarily lost the video signal. Is this normal?

---

### Post by mrfelker on 2016-04-21
This post saved me 4-5 hours after installing Paragon ExtFS on dual boot system Windows 10/openSUSE Tumbleweed.
touch  /forcefsck seemed reasonable but did not work to enable Authority. 
I also commented out two drives I probably should mount manually.

---

