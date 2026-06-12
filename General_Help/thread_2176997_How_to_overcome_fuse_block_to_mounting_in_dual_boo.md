---
title: "How to overcome fuse block to mounting in dual boot machine"
date: 2013-09-26
forum: General Help
---

### Post by andrewkirk on 2013-09-26
My PC dual boots Ubuntu and WinXP. The PC is about to be thrown out, having unresolvable hardware problems. But all my data is on a 'Data' partition of the hard drive (separate from the Windows and Ubuntu partitions), which works fine. I want to save the hard drive and use it in a new machine, or at least copy the data. The trouble is that because of the hardware problems Ubuntu no longer works on the PC - all I can get is the root shell from Recovery boot mode, WinXP seems to work OK but it never shuts down properly. The consequence of that is that I cannot access the Data partition from linux root shell on the PC. When I try to mount the partition I get a message that mount is denied because the NTFS volume is already wexclusively opened. 

I need to access the partition from linux because Rhythmbox gave some podcast directories names that include characters that are illegal in NTFS, like ":". I need read-write linux access to the partition to fix those directory names, but I can't get it because I am blocked by fuser. I can't change the names in XP because while it will show me the directory name it won't let me change it. I tried unmounting the partition in XP and then powering down but fuser still blocked my mount attempt when I booted into linux root shell.

I tried changing the directory names throufgh the network on a client computer running Ubuntu but the Windows PC, acting as server, would not even serve the (illegal) directory name to the linux client. So I can't access it that way.

Can anybody please suggest how I can override the block to my mounting the Data partition in linux root shell?

Thank you very much.

---

### Post by Bashing-om on 2013-09-26
andrewkirk; Hi !

How about accessing that drive from a liveDVD, and from there launching "nautilus" as:
terminal code:
```

gksudo nautilus

```
else from that liveDVD, what does "fuser" report ?
```

fuser -m /dev/sdXY

``` where 'X" is the drive letter, and "Y" is the partition number where you are attempting to access.
Which should list a Process ID
```

ps aux | grep <PID>
kill -9 <PID>
umount /dev/sdXY

```
that should work.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by andrewkirk on 2013-09-27
Thank you bashing-om

Unfortunately I can't use the LiveDVD because the PC crashes with that due to the hardware problem.

I have tried using your fuser suggestion from the root shell available from the recovery option in GRUB. It returns a list of about 8 processes. I kill them one at a time, and some of them stay dead, but some of them just reappear immediately. Process PID 1 is always the first in the list. When I enter 'kill -9 1' it accepts the command without complaint and gives me a new prompt, which I assume means it killed it. But then when I do 'fuser -m /dev/sda5' again it is is still there as the first on the list. There are usually two process with PIDs in the 800s that do the same. Other processes make the screen go funny when I kill them.

I never seem to be able to get the list of processes using the volume below five elements, and I can never get it to mount the volume - always the same message that the volume is being used.

By the way when I try to unmount the volume by 'umount /dev/sda5' it tells me the volume is not mounted (which is what I'd expect).

I feel stumped!

---

### Post by Bashing-om on 2013-09-27
andrewkirk;

What to say ! A trying situation for sure.
PID #1 is the number one process running and controls almost everything ! Can not be killed;
Fuser must be ran from an outside means ..as in a liveDVD or an alternate install;
I'll bet that the Windows' partition has a lock on it from Windows, and best released with Windows' procedure/tools  .

In order to do any thing conclusive you must have a means to boot a live environment, and at the very least look at the disk(s) with ubuntu's partition editor "GParted", maybe get a handle on what is not going on. If you have a spare hard drive lying about AND can boot a install medium, here is one sure way to get to your data. This will give you a way to boot the system and allow a means to maybe unlock that partition (??)

Specifically, why can not you boot from a liveDVD or liveCD ? One has to boot up the system from some source !

1) Remove this drive from the machine
2) Install Windows to a new drive
3) Re-attach this drive as a 2ND HDD and try to access it in Windows
4) If the drive shows up:
4A) Copy your data off immediately
4B) If the files don't show up, run a Windows' recovery utility to see what files can be recovered.
4C) If there is no hardware failure on that hard drive, might use ubunt's "testdisk" utility to recover the files.

If it is indeed a hardware fault on that hard drive, professional (expensive) expertise is is order. They would Remove that physical disk from the enclosure and install that disk into  another enclosure to recover the data.

[INDENT]where there is a will there is a way, not saying it is easy ![/INDENT]

---

### Post by oldfred on 2013-09-27
From XP can you run chkdsk on your data NTFS partition. It may be d?

       chkdsk d: /r


 You can use the following options:
/p Does an exhaustive check of the drive and corrects any errors.
/r Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. 
      
 [http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

If drive has huge issues chkdsk does move damaged files to its own temp directory.

---

### Post by YannosB on 2013-09-27
perhaps because of the HW problems, you can 'walk around it' via a usb stick with a live grub boot. I have found several that work linux, and Win mini's.. google Live USB, rescue USB, that will get you on teh path. The HW issues should not be able to block USB booting (unlike CD/DVD).

---

### Post by andrewkirk on 2013-09-28
Thanks for the suggestions. I have pursued it a bit further using those.

The reason I can't use a LiveCD is that the HW problem seems to cause crashes whenever X11 is activated, so I need a non-graphical environment.
I found an old 'linux rescue CD' that can be used to boot into a command line linux kernel and ran that. That worked fine and allowed me to mount the volume, which is definite progress (as previously it wouldn't even mount with read-only access). The mount worked because I could list and read the files. However I realised when I tried to rename the offending directory that it was only mounted read-only. I unmounted and remounted a few times, using 'mount -w /dev/sda5 /root/temp' but although it didn't complain about the command and returned a friendly prompt, it only mounted it as read-only, as I discovered when I tired to rename the dir.

I have found a fix that works for now. I can boot the PC using a Puppy Linux CD, which seems to have low enough resource demands not to run into the hardware problems, but high enough sophistication to give me write access to the volume. So I have now managed to rename the dir with the offending characters.

I would still value any suggestions as to how I can, from the command line in the linux rescue environment, force it to mount the volume as read-write, or at least get a message back to tell me why it won't. 

thanks again

---

### Post by Bashing-om on 2013-09-28
andrewkirk; Hey ;

If the primary objective at this time is to recover the data on that hard drive, may I suggest that you look at the utility "testdisk". Several ways to deploy it .. might be best to burn it to a bootable CD. Lots of guides are available ... google is our friend .. search term "testdisk ubuntu" gives lots of hits !

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by Habitual on 2013-09-28
[This]("http://puppylinux.org/wikka/ntfs3g") says puppy   will mount it ro.
I presume you know how to umount. ;)

```
# mount -t ntfs-3g /dev/your-NTFS-partition /{mnt,...}/folder rw
```
should work.

Edit: If you aren't familiar with umount, it's
```
# umount /mount/point
```

---

### Post by oldfred on 2013-09-28
Ubuntu recovery mode should also let you get to a command line.

When mounting NTFS with fstab you should include the windows_names setting to avoid the illegal characters.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

### Post by Habitual on 2013-09-28
Thanks oldfred:

I forgot about UUIDs as I don't use Ubuntu.
I didn't mean to cause the user any more grief by passing along inaccurate instructions.

Peace.

Edit:Sun Sep 29, 2013 - 2:44:18 PM EDT
NOTE: You should use UUIDs for mounting partitions.
Please review and be comfortable with this [document.]("https://help.ubuntu.com/community/UsingUUID")

---

