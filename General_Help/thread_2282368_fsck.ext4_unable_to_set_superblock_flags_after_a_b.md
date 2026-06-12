---
title: "fsck.ext4 unable to set superblock flags after a bad unmount?"
date: 2015-06-13
forum: General Help
---

### Post by Geo_Ragusa on 2015-06-13
Hello there! This is my first time posting here on the forums, though I've spent quite some time here in the past (mostly while troubleshooting issues on my own). It's been a great resource, and up until now I've been able to solve all of my own problems with just a bit of searching, but it seems luck's run out on that one, unfortunately.

Straight to it, then. I run Ubuntu 10.10 on my laptop, as it's too old and weak of a machine to handle newer Unity-enabled versions. Even with this, it's been running into more and more trouble over the years, as software like Firefox and resource-hogging site designs have been pushing it hard (only 1GB RAM to work with). More recently, it's been causing the system to hang due to RAM usage going too high, and forcing manual shutdowns to get out at all. Not a good thing.
To make a long story short, occasionally these shutdowns cause data loss, requiring the use of a live CD to get into the terminal and run fsck manually so the partitions can be mounted again. This last time however went one further, and now even that isn't working.

Running ```
fsck -y /dev/sda2
``` returns a result like this:
```
[COLOR=#000000][FONT=verdana]/dev/sda2: recovering journal[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Superblock needs_recovery flag is clear, but journal has data.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Run journal anyway? yes[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]fsck.ext4: unable to set superblock flags on /dev/sda2[/FONT][/COLOR]
```

My system is partitioned with a boot, root, and home on separate partitions. The boot partition has errors as well, but fsck runs on it without an issue; the root and home partitions both return the same "unable to set superblock flags" error every time however, regardless of what I've tried. (I've also tried using backup superblocks, but it seems those aren't the problem, since it returns the same result.)

The annoying - and relieving - thing is that, when I hook the laptop's HDD up to my Windows rig, I'm able to use an ext4 reading software (I used DiskInternals Linux Reader) to get into the partitions in read-only mode, where all of the data is present and intact. The partitions simply refuse to be mounted in any other manner, even though they're otherwise perfectly fine.
This is actually the second time the HDD has run into this "unable to set superblock flags" issue - the previous time being two days ago - but the first time around, plugging the HDD into my Windows rig and running the live CD from there somehow got it working again. Retracing my steps hasn't had the same luck this time.

I don't have access to my terminal logs at the moment, but I can pull up any that are needed by request, to try and help shed some light on things. All of my data is backed up currently, so the only thing a re-installation would cost is the loss of programs and settings, but I'd like to leave that as a last resort; all of the data on the partitions appears to be there, so I'm hoping there must be some way to force it to set superblock flags or otherwise get it running again.

Any advice would be greatly appreciated!

---

### Post by oldfred on 2015-06-13
You should try to do R-E-I-S-U-B shutdown if at all possible. Remember the Elephants. 
       Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is (exact order of middle commands not critical).
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

I do not know if e2fsck is really any different than fsck.

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

      
 [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

### Post by Geo_Ragusa on 2015-06-13
I'm going to spoil the ending and just say that you are a lifesaver. Though the unfortunate thing is, after all of that, I'm not sure what actually fixed things... I'll try to list as much as I can anyway, in case it helps someone else out.

> **oldfred said:**
> You should try to do R-E-I-S-U-B shutdown if at all possible. Remember the Elephants. 
       Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is (exact order of middle commands not critical).
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)

Never knew about that! A little unwieldy - my fingers have trouble stretching to so many buttons all at once, since my laptop doesn't have a numpad and thus requires the Fn button to also be held down - but considering the frequency of the system lockups at this point, I don't think I'll have any difficulties getting that memorized.

> I do not know if e2fsck is really any different than fsck.

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

      
 [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda5 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5
One user could not get partition unmounted (may have needed swapoff), but used another live distro

here are the results of the above commands. Note that "Ubuntu_10.10" is the name of my system's root partition (dev/sda2), just to avoid any potential confusion that might cause.
```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda2
Ubuntu_10.10: recovering journal
Ubuntu_10.10: Superblock needs_recovery flag is clear, but journal has data.
Ubuntu_10.10: Run journal anyway

Ubuntu_10.10: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
     (i.e., without -a or -p options)
```
```
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda2
e2fsck 1.42.9 (4-Feb-2014)
Ubuntu_10.10: recovering journal
Superblock needs_recovery flag is clear, but journal has data.
Run journal anyway? yes

e2fsck: unable to set superblock flags on Ubuntu_10.10

Ubuntu_10.10: ********** WARNING: Filesystem still has errors **********
```

Now, I read through the links provided, tried a few different things in there as well but mostly the same results (running *sudo fsck -yv /dev/sda2* had an interesting result the first time - dumped a bit of text about clearing orphaned inodes, then deemed the drive clean - but this didn't do anything on the other partitions, and returned to its usual "unable to set superblock flags" when trying to run it a second time on the partition). Not sure what that means, all I know is it didn't actually fix anything. Moving along...

The "debugfs" command didn't seem to do anything either (just realized now that this is because I copied the command exactly as the other user had it, but theirs was intended to fix an ext3 partition, not ext4 like mine is), so I moved ahead to trying to run "fsck" with a backup superblock, which again, pretty much same results as posted above:
```
ubuntu@ubuntu:~$ sudo fsck -y -b 32768 /dev/sda2
fsck from util-linux 2.20.1
e2fsck 1.42.9 (4-Feb-2014)
Superblock needs_recovery flag is clear, but journal has data.
Recovery flag not set in backup superblock, so running journal anyway.
Ubuntu_10.10: recovering journal
fsck.ext4: unable to set superblock flags on Ubuntu_10.10

Ubuntu_10.10: ***** FILE SYSTEM WAS MODIFIED *****

Ubuntu_10.10: ********** WARNING: Filesystem still has errors **********
```

I tried a number of backup superblocks in order, but all of them gave the same output, sadly. However, I decided on a whim to try and reboot anyway - actually, I was trying out the REISUB method - and lo and behold, busybox is nowhere to be seen and fsck runs itself on the boot screen. Everything is currently functional as though nothing had happened. Horay for technology!

If I had to take a guess, the fix came from one of two things. One, *sudo fsck -yv /dev/sda2 *stood out as the only command that gave an actual output of things happening, even though it stopped working immediately afterwards. Since it did this on the root partition, that may have been the kick needed to get past busybox and let the automatic check fix the home partition. Two, the alternate superblocks didn't seem to show anything happening, but it's possible that one of them *did*
actually have an effect, which led to the system's revival upon reboot.
The only other thing I've been able so far to decipher regarding this whole issue is that another cause - besides the improper shutdown - is simply faulty hardware. With a laptop that's somewhere around five years old now, this seems somewhat likely as an additional culprit, and it may simply be luck and persistence that save it. I haven't seen any other issues with the HDD though so I'm inclined to believe it's primarily a data issue however, if only because that's a more comforting thought.

In any case, I hope REISUB will serve as some protection against future issues of the sort.

---

### Post by oldfred on 2015-06-13
Glad whatever worked, but I would make sure to have good backup procedures.

---

### Post by Geo_Ragusa on 2015-06-14
> **oldfred said:**
> Glad whatever worked, but I would make sure to have good backup procedures.

Yes, definitely. I'll be keeping everything even the slightest bit important backed-up on a USB drive, and I already have a few other things in Dropbox.

Worth noting that after all of the above, there were some casualties, possibly a result of messing around a little too much with /dev/sda2; so far all I've found is that running SM Player (MPlayer frontend) causes the system to hang the moment it tries to open, requiring REISUB to get out of it. MPlayer runs fine and removing/re-installing SM Player didn't do anything, so I suspect there might be some little block in there that got messed up or something, and I'll possibly find other errors down the road if I leave the partition as-is. Not a comforting prospect, but the important thing is everything else seems to be intact and everything can be backed-up or copied over as needed now without having to completely start fresh!

Thanks again for your help.

---

### Post by oldfred on 2015-06-14
If just one application hangs, you often can still open a terminal. 
Then in terminal run 
top

That will show you all your processes and you can run this to stop a process.
sudo kill xxxx
Where xxxx is number of process you want to kill.

see also 
man kill

---

### Post by Geo_Ragusa on 2015-06-14
> **oldfred said:**
> If just one application hangs, you often can still open a terminal. 
Then in terminal run 
top

That will show you all your processes and you can run this to stop a process.
sudo kill xxxx
Where xxxx is number of process you want to kill.

see also 
man kill
Boy, it feels weird to intentionally open something you know is going to lock up your computer.

Unfortunately, it didn't work (though it's yet more info I'll be sure to keep handy). Terminal won't even open, nor will anything else, though the mouse can still be moved and items can be clicked (with no visible results). I keep my CPU usage and RAM usage graphs on the taskbar, and what happens when I try to open SM Player (and only SM Player causes this, so far) is the CPU usage jumps to 100% and stays there. Leave it for a little longer or try to do something else, and eventually even the graph stops updating.
I had intended to install Ubuntu MATE on a second partition, then try to copy over my programs and their settings, so that's probably the safest way to go right now short of just getting a new laptop. It was also suggested to me that I try Lubuntu since the hardware has such low specs, so that may be safer still. It just has my curiosity piqued now; there's a solution to everything, even if re-installing is probably more efficient in a lot of these cases...

---

