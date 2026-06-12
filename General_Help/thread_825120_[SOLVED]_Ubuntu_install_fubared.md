---
title: "[SOLVED] Ubuntu install fubared?"
date: 2008-06-10
forum: General Help
---

### Post by PoopyTheJ on 2008-06-10
Ok, so we had a power outage last night and I rebooted and ubuntu seemed to be operating just fine except when I tried to run a movie in sections it lagged for a bit with heavy HDD ativity but it resumed and I thought little of it. Today I logged on and noticed that pidgin was acting very odly, wouldn't send messages the window was all blank after trying to send a message and I thought I'd kill the process and restart, then I couldn't start the system monitor. I figured hmm, somethings od and rebooted, upon reboot I get these kinds of error messages in terminal no gui has loaded yet,


ata1.00 exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
Buffer I/O error on device sda2, logical Block 23049

These messages scrolled down the screen for about 10 minutes and now the machine has a blank black screen with heavy HD activity. Now no HDD activity but still a blank black screen. Sda2 is a wholly ntfs partition on a 160gb drive, sda1 is broken up into a 25gb windows partition a 20gb ubuntu partition, a 208gb home partition and a 2gb swap. Have a dual core e4600, 4gb ram, Radeon 3850HD. Any advise? Any way to fix this or am I screwed?

Just noticed there is a little orange or light brown ASCII star in the left hand side of the screen. Shutting off till I figure out what to do.

---

### Post by ModelM on 2008-06-10
You might try booting into the live cd & doing manual file system checks from there of each file system. The command is fsck.

---

### Post by PoopyTheJ on 2008-06-10
just fsck? or is there something that comes after it?

---

### Post by PoopyTheJ on 2008-06-10
when I open the terminal in live and type fsck I get fsck 1.40.2 (12-Jul-2007) returned but it does nothing, even with the -a option I get the same thing returned but no action. What option do I need to set in order to get this to run and check the hard disks? do I need to use like fask sda1 or?

---

### Post by Herman on 2008-06-11
Hello PoopyTheJ              ,
I prefer to run e2fsck rather than just plain fsck if it's an ext2 or ext3 file system.
Something like 'sudo e2fsck -C0 -p -v -f /dev/sda1' is a good one to begin with. 
```
sudo e2fsck -C0 -p -v -f /dev/sda1
```That sorts most problems out, it's quite an effective command, but it's a nice safe everyday, general purpose command, it won't hurt anything.
If that one doesn't fix it for you though, you might need to brace yourself and try something a little stronger.
Try out this link and see if it helps you, [Running a filesystem check on an ext3  filesystem.]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem")

---

### Post by PoopyTheJ on 2008-06-12
ok, I tried running that command and I get this message,

ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -v -f /media/disk
e2fsck: Is a directory while trying to open /media/disk
/media/disk: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


The disk is ext3, am I setting some parameter incorrectly or will e2fsk only work with ext2? I'm researching e2fsck but really unfamiliar with it... Any advise?

---

### Post by PoopyTheJ on 2008-06-13
as an update I tried this sudo dump2fs /media/disk to find backup superblocks and got this error message,
 dumpe2fs /media/disk
dumpe2fs 1.40.2 (12-Jul-2007)
dumpe2fs: Attempt to read block from filesystem resulted in short read while trying to open /media/disk
Couldn't find valid filesystem superblock.


I also cannot copy the items from my home directory as I don;t own them to back them up I tried

chown ubuntu /media/disk-1 but it says the comand is not permitted, now that it appears as though my install is totally fubared and I'm a complete newb with this checking stuff if I can't check it I'm wondering if I just reinstall and reset sda5 as my home directory, which is how it shows in the installer will I still have my home directory if I choose the same user name? I can reinstall my programs but I can;t lose the data on my home partition...

---

### Post by Herman on 2008-06-13
```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -v -f [COLOR=Red]**/media/disk**[/COLOR]
```Probably it's because you used '/media/disk' there instead of Linux device notation.
You should run 'sudo fdisk -lu' to see what devices you have and what Linux calls them.
```
sudo fdisk -lu
```If your Ubuntu partition is '/dev/sda2', then try the same command again, but replace '/media/disk', with '/dev/sda2', or something similar, depending on the output from 'sudo fdisk -lu'.
```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -v -f [COLOR=DarkOliveGreen]**/dev/sda2**[/COLOR]
```

---

### Post by PoopyTheJ on 2008-06-13
Ok that fixed it, though I'm having all sorts of bizarre issues with Ubuntu now, firefox greys out when trying to load a new page, avant crashes in wierd ways, x server crashes due to some internal error etc, I think I'll probably reinstall gutsy, though I hate to lose my new shiny OSX like interface ;)

---

