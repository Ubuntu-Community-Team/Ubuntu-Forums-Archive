---
title: "UUID adventure"
date: 2006-12-28
forum: General Help
---

### Post by reiki on 2006-12-28
This whole UUID thing is a real pain in the rear. I understand there are reasons for it, but it really goes againt the whole "for humans" part of Ubuntu. Not so much because it is THERE.... but because there's precious little documentation on it. This might be a bit long, but I am going to tell my tale here about how UUID bit me in the butt.....

I had 2 drives in my system. One was IDE (/dev/hda1) and the other was sata (/dev/sda1).
The IDE drive had Edgy on it and the SATA drive has Dapper on it. 

I got a new SATA drive for christmas. I installed it.... now the fun begins...

I installed Edgy on the new sata drive (/dev/sdb1) but was having problems getting it configured like the Edgy on the IDE drive. Not wanting to go through all of my previous trials and tribulations getting Edgy working (very well, by the way), I decided to simply clone the IDE drive onto the new SATA drive.

In BIOS my first hard drive is the first SATA drive, second is the IDE drive, third is the second SATA drive. So GRUB is being read from the first SATA drive. I spent some time in grub's menu.lst getting things to point to the right places. OK... so Dapper boots properly.... then I got Edgy on the IDE booting.... however Edgy on the new SATA drive would not come up correctly.  

Finally I would get Edgy to boot, but on checking (using teh mount command) I found that what I THOUGHT was Edgy on the second SATA drive was actually Edgy on the IDE. Maddening. Learned more about grub than I wanted to.... grub > find .... *sigh*. Actually installed grub again on the IDE drive just to see what it would do and.... grub guessed wrong at my hardware. hd0,0 is my first SATA, hd1.0 is the IDE, hd2,0 is the second SATA. Grub had hd0,0 and hd1,0 swapped. Ok so that wasn't going to work. 

Went into fstab on the second sata. The entry telling it where the root was used the UUID. I checked UUIDs. Hmmm.... /dev/hda1 and /dev/sdb1 had the same UUID. So much for unique IDs, huh? Now I KNOW this was my fault for cloning. But now... how do I change it? And where?

There doesn't seem to be a simple tool for just straightening out the UUID mess. Cloning drives is not unusual. Moving drives is not unusual. Here are some of the things I ended up doing...

use ls /dev/disk/by-uuid/ -l to see what UUIDs were associated with what devices. Not all devices were in there. Kinda odd.... again probably due to my clone job.

blkid shows you what it THINKS are the UUID to device associations. You can get different results from this than what you see in the previous command. (Nice, huh?)

What I ended up determining was that /dev/hda1 and /dev/sdb1 had the same UUID. Not surprising.... cloned. 

I used uuidgen to generate a new UUID
I used tune2fs -U to assign that new UUID to /dev/hda1

blkid didn't show the change. Hmmmmm.... I rebooted.
blkid STILL didn't show the change but using ls /dev/disk/by-uuid/ -l clearly showed the change.
Turns out blkid was reading a cachefile at /etc/blkid.tab and even after reading the man page for blkid, nothing I did would get it to rewrite the cachefile. So I renamed it. Ran blkid..... no results! It had nothing... AND it didn't recreate the cachefile. OK.... so I did sudo blkid. THAT worked.

I've got UUIDs for all data partitions now and 2 out of 3 swap partitions (no idea.... don't ask).

In fstab on the new sata drive, I REPLACED the UUID part of the entry for root with the old style /dev/sdb1 type... that still works fine.  At some point I may try changing that back to the UUID entry and see if it works properly.

All in all.... this sucked. I spent a LOT of time on this and came away with the feeling that this is why I didn't use linux many years ago. No, I'm not leaving Ubuntu, but I sincerely hope the devs will keep the "for humans" part in mind when they make changes. Keep in mind that we need the tools to keep up with the advancements. 

For example.... a tool that looks at hardware, checks to see if it has a UUID already (perhaps in /dev/disk/by-uuid) and if it does NOT have a UUID, create one, assign it, and then check wherever is necessary (for example , in fstab) to see if that device is referenced and fix the UUID there. 

And here's a scary thought... I did all this just to get my Edgy on the new sata working. What about Edgy on the original IDE? What about Dapper on the first sata? I don't think Dapper knows about UUIDs yet so probably not an issue, but.... I don't want to do this again. I think I'm just going to have Dapper for stability, Edgy on sata2 for ....well because I like it.... and remove Edgy from teh IDE and use that for storage and/or testing stuff.

See what I mean about long? This whole UUID thing was a big pain in the rear end.

---

### Post by kidders on 2006-12-28
Hi there,

Perhaps I'm misinterpreting your post, but it seems as though you are complaining that a hard disk you cloned was actually cloned, rather than approximately duplicated. :-k 

Filesystem UUIDs exist, in part, to facilitate exactly the behaviour you described, in that a clone of another filesystem can be made to behave exactly as the original did, regardless of it's physical location on your motherboard. This is tremendously convenient, as it allows people to move hard disks around without having to worry about reconfiguring /etc/fstab, etc. On the other hand, plugging both the clone *and* the original into your system simultaneously would almost be like giving two computers the same IP address and plugging them into your LAN.

---

### Post by reiki on 2006-12-28
kidders,

nah.... I understand why teh UUIDs are there and how they can be beneficial, but there needs to be a way to .... I don't know.... straighten them up I guess for lack of a better term, when we make changes. 

For instance.... the UUIDs are now apparently all ok on the drive I use to boot.... /dev/sda1 ...

But what happens if I want to make /dev/sdb1 the boot drive? There should be a way to get all of the UUID information onto that drive easily. And not by copying from /dev/dsa1, because what if /dev/sda1 had died? See what I mean?

I'm thinking of a tool like.... lets-rebuild-all-the-UUIDs.sh .... or .... something. :)

---

### Post by bulldog on 2006-12-28
Try this in a terminal,:D   ```
ls /dev/disk/by-uuid -lh
```

Works like a charm over here.

---

### Post by kidders on 2006-12-28
> **reiki said:**
> But what happens if I want to make /dev/sdb1 the boot drive? There should be a way to get all of the UUID information onto that drive easily. And not by copying from /dev/dsa1, because what if /dev/sda1 had died? See what I mean?

I *think* I'm with you. It sounds as though you'd like an easy way to make one filesystem pretend to be another, by stealing it's UUID.

While I can certainly see your point, it seems as though you're trying to mix the behaviour you get from referring to filesystems using their /dev paths with what you get when you use their UUIDs. The trouble is that one is designed to *ignore* the substitution of one filesystem for another, while the other is designed to *prevent* it. Conversely, one tries to make the physical location of a filesystem irrelevant, where the other depends completely upon it.

I suppose that, if you're the sort of person who likes to make frequent changes to his disk layout (like I am!), you'll invariably have to do things like tweak your /etc/fstab from time to time. Whether you use UUIDs or /dev paths to reference partitions depends on which circumstances you want *not* to have to make those updates in ... if you know what I mean.

On my PC for instance, I quite frequently rewrite my swap space, so I use /dev paths to reference my swap partitions, since their UUIDs change more often than my underwear. :-? I use UUID notation for certain external devices though, since their /dev paths are harder to predict. That way, in terms of the number of annoying tweaks I have to make, I get the best of both worlds.

Does any of that make sense ... or help?

---

### Post by reiki on 2006-12-28
Bulldog,

using ls /dev/disk/by-uuid -lh works fine IF they are all represented in /dev/disk/by-uuid. In my case some partitions were simply not there and 2 had identical UUIDs (because of cloning, I'll admit). 

kidders,

I think what I'm looking for.... maybe a better description... is a tool that will "take inventory" of partitions, see if they have a UUID, and if they DON'T have a UUID, create and assign one, AND check for duplicate UUIDs (if they are supposed to be unique, then the fact that 2 drives had identical UUIDs should not have been able to happen, even as a result of cloning), AND check that references to these various partitions/drives/filesystems...whatever... are correct. 

And you are correct. I still do not have a thorough understanding of the mechanics of UUIDs. For instance... is the UUID of /dev/hda1 stored ON THAT DEVICE someplace? If so, I could simply query a device to find its UUID ( like.... what-is-your-UUID /dev/hda1 ... ).

In /dev/disk/by-uuid we find symlinks that point to devices. The symlink name contains the UUID. THAT, in and of itself, doesn't seem very special. 

Discussing this is helping me to formulate the questions that, if answered, may help me understand better...

If I simply swap 2 drives, let's say I swap /dev/hda and /dev/hdb. The symlink in /dev/disk/by-uuid still has the UUID of the (original) /dev/hda1 pointing to /dev/hda1 which is now the former /dev/hdb1. How does the uuid that was pointing to /dev/hda1 now know that it should be pointing to /dev/hdb1?  

OK that last bit was confusing to read back, but hopefully it will make sense. Perhaps more simply put.... if UUID 12345-1234 is associated with /dev/hda1 at the time the UUID is created.... by what mechanism does it follow that file system when the file system is physically relocated?

Your external device is a great example. Let's say you have an external hard drive, USB, 40gig, and you plug it in. First of all does it automatically get a UUID? Ok it's the only thing plugged in to USB. It has a UUID. You unplug it. Later you plug a DIFFERENT USB hard drive, 80gig, into that usb port. It gets its own UUID? From where? And now, while that USB hard drive is plugged in you now plug in the OTHER USB hard drive. It almost certainly has a new device name and isn't even plugged in to the same USB port that it was when it got its UUID. HOW does the system say to itself, "Oh that's UUID 12345-1234. I know that's the 40gig hard drive that was here before"

There... I think that last bit was more clear in practical terms.

---

### Post by bulldog on 2006-12-28
I wild guess,but is the UUID not something what's written on a particular partition?
So you can swap drives to another but still keeping the same UUID?

Did never lose any sleep about this,but now I want to know,.....thank you very much:mad: 

:D :D

---

### Post by kidders on 2006-12-29
> **reiki said:**
> Is the UUID of /dev/hda1 stored ON THAT DEVICE someplace?Yes, it is. You can query a filesystem with **vol_id -u /dev/hda1**.

> **reiki said:**
> In /dev/disk/by-uuid we find symlinks that point to devices. The symlink name contains the UUID. THAT, in and of itself, doesn't seem very special.It's a convenient way of connecting UUIDs to device names without actually having to probe anything.

> **reiki said:**
> If I simply swap 2 drives, let's say I swap /dev/hda and /dev/hdb. The symlink in /dev/disk/by-uuid still has the UUID of the (original) /dev/hda1 pointing to /dev/hda1 which is now the former /dev/hdb1.That shouldn't be happening. Are you sure this isn't related to your disk cloning experiment?

> **reiki said:**
> If UUID 12345-1234 is associated with /dev/hda1 at the time the UUID is created.... by what mechanism does it follow that file system when the file system is physically relocated?

[LIST]
[*]Filesystem identifiers are intended to be universally unique, so you should be able to move one from one computer to another, and refer to it using its UUID, happy in the knowledge that conflicts probably won't arise. This means, for instance, that you can swap an entire RAID array into a new machine, simply duplicate it's configuration info, and trust that it will work.
[*]UUIDs are read from a drive when udev analyses your hardware, and used to make /dev symlinks.
[*]UUIDs are normally assigned when a filesystem is created.
[*]UUID conflicts will (and should) arise if you clone a filesystem. You should not, however, expect your system to do sensible things if you intentionally plug multiple filesystem clones in at the same time.
[/LIST]

The tool you're describing is interesting, but there would be a few problems with it, I think. Creating or rewriting UUIDs automatically could impact filesystem operation in ways the tool could not foresee ... for instance, would affected disks would continue to work in other computers they may be being used in? In addition, how would the tool determine that the apparent duplicate filesystem was not created deliberately, with the intention of removing it, and keeping it as a backup.

As I mentioned before, try to think of UUIDs as though they were IP addresses. They will usually be unique, unless you deliberately misconfigure things. If you were managing a HA network, you might create replicas of certain critical machines, that you could plug into your LAN at a moment's notice, in the event of a failure. If you were to plug two clones into your network simultaneously, they would both conveivably try to offer the same services at the same IP address, and make a mess.

---

### Post by reiki on 2006-12-29
I think I'm beginning to understand this better. The UUID is stored in the file system header. It is retrievable using vol_id devicename because vol_id know where in the header to look. THAT I can understand. 

If I'm understanding you correctly, kidders, when I start my machine the system checks hardware for UUIDs and then, if necessary, rewrites the symlinks in /dev/disk/by-uuid.

That's pretty cool actually. 

I have found the UUIDs of all of my partitions now. Because of cloning, I had to create and assign a new UUID for the cloned drive. You're right... the clone job worked perfectly! :)  Having done that I then made the necessary edits in fstab and... well... I must have done them ok because it's all working.

Thank you and Bulldog for your patience and helping me to get a better understanding of this.

---

### Post by kidders on 2006-12-30
Hey again,

Happy to help :-)

I just thought I would add one more thing...

Another way of duplicating filesystems is just to "cp" files from one place to another. For instance, you could create & format a partition yourself (say /dev/sdb1), and copy /dev/sda1 into it with something like **cp -dpR /mnt/sda1/* /mnt/sdb1**. This approach has a few advantages, depending on what you happen to want:

[LIST]
[*]UUID-related issues don't arise.
[*]Source and destination partitions don't have to be the same size.
[*]Source and destination filesystems don't have to be of the same type.
[*]You only duplicate data ... not it's relative physical location ... so your destination copy is effectively a defragmented version of the source copy.
[*]You can combine the "cp" with a "find" to avoid wasting time duplicating temporary files, for instance.
[/LIST]

But then again... sometimes a "dd" is just easier!

---

### Post by JohnnyVW on 2007-04-23
OK, OK...  Now *I'm* really confused...

I used a Live-CD to copy one disk to another.  I upgraded to a larger hard drive.  So, I used **cp -dpR /mnt/olddrive /mnt/newdrive**  I removed the old hard drive and inserted the new on in it's place.

I had to tweak grub, grub.menu and fstab to point to the new drive. (I'm dual-booting XP and Ubuntu).

So, am I to understand that the UUID is for the device?  In other words, olddrive has a UUID of 12345-67890 and newdrive has 09876-54321 (for example)?

It looked like if I used cp to copy ALL of the files over, it would be seamless.  Not so much in my experience.

My next project is to do it again...  on an even bigger drive, but that's for another topic...

---

### Post by kidders on 2007-04-23
Hi there,

Pretty much everything has a UID of some sort ... your mouse, USB ports, hard drives ... The identifiers *we're* talking about belong to filesystems (ie _not_ hard drives, partitions, IDE interfaces, etc.) Linux is (optionally) able to use unique IDs to identify parts of your system, so it can perhaps be instructed to treat certain things differently.

A common way of using filesystem UUIDs is in /etc/fstab, so that (among other reasons) the physical order in which your disks are connected to your I/O bus becomes irrelevant. The problem the o/p seemed to be having is that a byte-for-byte copy of a filesystem will, by necessity, have the same UUID as the original, which has the potential to cause problems, should he plug both into his computer at the same time. (Think of it in terms of what might happen if you plugged two NICs with the same MAC address into the same network, and then tried to communicate with one of them.)

> **JohnnyVW said:**
> I had to tweak grub, grub.menu and fstab to point to the new drive. (I'm dual-booting XP and Ubuntu).That's normal. Depending on where your bootloader lives, you may have been able to avoid making tweaks by *not* using UUIDs in your /etc/fstab.

> **JohnnyVW said:**
> So, am I to understand that the UUID is for the device?Yes and no. Both your storage devices *and* the filesystems on them have their own UUIDs, for use in a variety of ways.

I hope that helps a little.

---

### Post by JohnnyVW on 2007-04-23
Ahhhhhh!  Gotcha!  

So, it's not an "either/or" thing, it's an "and" thing.  

So, if I use dd or cp to copy an entire installation to a new drive, the UUID for the file system stays the same, but the UUID for the new hard drive is different from the old one.  

That explains why grub et al had to be tweaked.

Thanks!

---

### Post by kidders on 2007-04-23
> **JohnnyVW said:**
> So, if I use dd or cp to copy an entire installation to a new drive, the UUID for the file system stays the same, but the UUID for the new hard drive is different from the old one.

Not quite. Doing a raw dump of a filesystem (eg with **dd**) replicates it ... copying the files it contains (eg with **cp**) is not the same thing.

---

### Post by Omegatron on 2007-04-25
Is *this* why my partitions stopped being recognized when I upgraded to Feisty?  The partitions on my external drive were made with dd to backup my laptop's hard drive.  Would they have the same UUID then?  When I look at /dev/disk/by-path/, it shows 16 partitions, but when I look at /dev/disk/by-uuid/, it only shows 10.

---

### Post by kidders on 2007-04-26
> **Omegatron said:**
> Is *this* why my partitions stopped being recognized when I upgraded to Feisty?Possibly. It's important to remember that partitions don't have UUIDs though.

> **Omegatron said:**
> When I look at /dev/disk/by-path/, it shows 16 partitions, but when I look at /dev/disk/by-uuid/, it only shows 10.That's quite normal. /dev/disk/by-uuid will only list *filesystems*. On my box, for instance...

```
$ ls -1 /dev/disk/by-uuid/ | wc -l
5
$ ls -1 /dev/disk/by-path/ | wc -l
8
```

---

### Post by Omegatron on 2007-04-26
> **kidders said:**
> Possibly. It's important to remember that partitions don't have UUIDs though.

Filesystems do?

> That's quite normal. /dev/disk/by-uuid will only list *filesystems*.

Ok.

---

### Post by kidders on 2007-04-26
> **Omegatron said:**
> Filesystems do?Yep, that's right. For instance, here's more detail on the box I used for my last post. In red, I've written in the reasons some of the entries in one list don't show up in the other.

_/dev/disk/**by-path**_
pci-0000:00:1f.1-ide-0:0 -> ../../hda [SIZE=1][COLOR=Red][Not a filesystem][/COLOR][/SIZE]
pci-0000:00:1f.1-ide-0:0-part1 -> ../../hda1
pci-0000:00:1f.1-ide-0:0-part2 -> ../../hda2
pci-0000:00:1f.1-ide-0:0-part3 -> ../../hda3 [SIZE=1][COLOR=Red][Extended MS partition][/COLOR][/SIZE]
pci-0000:00:1f.1-ide-0:0-part5 -> ../../hda5
pci-0000:00:1f.1-ide-0:0-part6 -> ../../hda6 [SIZE=1][COLOR=Red][Part of a RAID Array][/COLOR][/SIZE]
pci-0000:00:1f.1-ide-0:1 -> ../../hdb [SIZE=1][COLOR=Red][Not a filesystem][/COLOR][/SIZE]
pci-0000:00:1f.1-ide-0:1-part1 -> ../../hdb1

_/dev/disk/**by-uuid**_
257fa038-8f98-4d3f-803b-c710bcb15962 -> ../../hda5
26FC01D7FC01A263 -> ../../hdb1
3beb69d4-7e6b-4610-a979-eaa1337c1ef2 -> ../../hda2
4d0a9770-0cdb-4ace-86f5-4a06e8c66def -> ../../hda1
b8e19ce7-949d-4128-9843-449d245e3984 -> ../../md0 [SIZE=1][COLOR=Red][Doesn't physically exist]
[/COLOR][/SIZE]

In any case, while I hope that helps make sense of things for you, none of it helps solve your problem! Yours may or may not be UUID-related. If you post some more details on your configuration & what won't work the way it should, I can try to help. :-)

---

### Post by Omegatron on 2007-04-26
> **kidders said:**
> If you post some more details on your configuration & what won't work the way it should, I can try to help. :-)

I hope so!

I started a new thread since I'm not so sure it's UUID related:

[http://ubuntuforums.org/showthread.php?p=2543667#post2543667](http://ubuntuforums.org/showthread.php?p=2543667#post2543667)

---

### Post by Omegatron on 2007-05-12
GRRRR.  I installed a second Ubuntu partition (Studio), and now my original one won't boot, because the UUID is not found.  Then it gave me a recovery console and when I told it to reboot it went into GDM instead?  And now it can't see any of my partitions.

**Why** did they switch to UUIDs again??

What program does the installer use to auto-detect the different drives and set up the fstab?  I just want to run that.  Especially because all my drives in the new installation are sda, but in this installation which I upgraded from Edgy, they're still listed as hda even though they're internally sda.  It makes no sense.

There's no reason why I should have to update the fstab myself.  There are partitions, they have filesystems; mount them.  This isn't difficult and there's no reason why the average user would want to change this.  If you want to set up RAID partitions, sure, but those people can learn to edit fstab.   For the rest of us it should just automount every partition on the system in a sane way.

---

### Post by kidders on 2007-05-12
> **Omegatron said:**
> There's no reason why I should have to update the fstab myself.  There are partitions, they have filesystems; mount them.  This isn't difficult and there's no reason why the average user would want to change this.  If you want to set up RAID partitions, sure, but those people can learn to edit fstab.   For the rest of us it should just automount every partition on the system in a sane way.
Checking /etc/fstab (and tweaking it where necessary) is something most users have *every* reason to do, really ... especially if Linux doesn't have the whole PC to itself. Trying to second guess users' intentions is non-trivial, when you think about it. For instance, forcing all detected partitions to automagically mount would be a _highly_ dangerous policy.

Just to reiterate:
[LIST]
[*]If you don't like using filesystem UUIDs, then don't. The choice is yours.
[*]The ability to make quick changes to the way Linux handles filesystems is one of its strengths. Linux users typically like to be in complete control of what their PC is doing.
[/LIST]

> **Omegatron said:**
> What program does the installer use to auto-detect the different drives and set up the fstab?It probably uses a one-liner (or something not very much longer) to mangle the contents of /sys/block into something intelligible.

---

### Post by Omegatron on 2007-05-13
When it screws up on boot, it says something like "apt-get is not installed.  use apt-get install apt".  Then it gives me a prompt, as if I had been logged in, but when I type something it just continues with the boot process?

---

### Post by ronodle on 2007-05-24
Man!  This is exactly what I _don't_ want to happen.  I have four hard drives with 7 different operating systems (or versions thereof).  When I boot I want _only_ the partition with 7.04 to be mounted at "/".  This thing automounts every partition in the machine no matter what I put in fstab.  If I can't get this sorted out I'll find a new use for this partition and it won't be another Ubuntu version.

Cheers,
Ron

---

### Post by ridgeland on 2007-06-21
My experience with my new Dell-Ubuntu E520N and UUID:
I changed the partitions on the hard drive right away.  I started getting three problems: incomplete shutdown, odd display like 8-bit color after a while, numlock LED on but numlock is not.  I doubt that I saw all the symptoms.  
I made lots of changes. I decided that turning off the BIOS's Fast Boot solved.  The problems went away.  Then I installed Fedora 7 and the problems came back!  How if Fast Boot was the problem and it was still off?
Exploring some more I saw F7 was using UUID and my Ubuntu partitions were using /dev/sdax.  I changed F7 /etc/fstab and /boot/grub/grub.conf to use /dev/sdax rather than UUID and the problems left.
So I turned Fast Boot back on.  The problems did not come back.
My conclusion:
UUID causes boot probems.  Maybe the UUIDs are too slow or late mounting and the PC is booting the first kernel it can find.
Whatever the reason for the problem the fix is avoid UUID.

---

### Post by kidders on 2007-06-22
That's certainly an odd experience!

It's important to note though, that UUIDs and /dev names are nothing more than two common ways of addressing devices. Which one (or what combination) a user chooses depends firstly on having an understanding of the differences between them, and then on which type of behaviour the user wants.

Neither addressing scheme is much more complicated than the other (strictly, I suppose, determining UUIDs may be slightly easier for a system to do), and both can cause booting problems, although usually not in the same ways/situations. For instance, UUID-based addressing is more robust to changes in the arrangement (or the OS's interpretation of the arrangement) of hardware, so where /dev-based addressing would cause boot failures, UUID-based addressing would often continue to function perfectly. Conversely, this kind of thing is not always desirable (swap filesystems are an obvious example), which is where /dev comes to the rescue. Calling one bad and the other good however is like calling the German keyboard layout bad and the French one good.

One general piece of advice I would offer is to make boot-related changes in small baby steps. I've often fallen into the trap of making large numbers of simultaneous changes that affect the boot process ... simply because performing reboot after reboot is tedious ... and it very often bites me in the a$$, without any way of determining which tweak created which problem. :-(

---

### Post by ridgeland on 2007-06-22
I can see how an IS department with 1000 PCs would like the interchageability of UUID.  For my home PC with two hard drives cut into 20 partitions the value of UUID is hard to find.  A hard drive crash is likely to take out 10 partitions.  Recovery will be via backups made to an external hard-drive.  Keeping the system up and running during the recovery would be meaningless.

My first encounter of UUID was SuSE using it.  I installed it multiple times.  I saw that swap had vanished on the older install.  This was due to UUID as the newer install had formatted SWAP and given it a new UUID.  Thus the old UUID was invalid and no swap space. /dev/hdax solved it.

UUID also makes for messier control files since the UUID is a long string you get line-wrap which is not as neat.

ed: Also with partimage I had new surprises as it copied the UUID, now I had two partitions with exactly the same UUID and no way to control what went where.  tune2fs can change the UUID, but I used /dev/sdax instead.

I guess I'm biased since I've only seen the negative side of UUID and not the positive.

---

### Post by Midahed on 2007-08-15
I've read this thread a couple of times and it still makes as little sense to me as general relativity :)

I think I can understand that cloning a drive (thereby creating duplicate UUIDs for the filesystems it contains) would cause problems.  The duplicate IP address analogy makes sense.  However, what would you expect to see in terms of UUIDs in a raid1 array?

The reason I ask is that a few weeks ago I installed an additional (new) drive in my PC and set-up the raid environment without doing a clean install of Feisty.  There are a number of fairly detailed how-to posts that spell out the principles:-

[I]Create the necessary raid1 partitions on the _new_ drive using sfdisk -d
Create the raid device and specify the original drive as 'missing'
Create a filesystem on the new raid device
Use cp to copy all files from the original drive to the new raid device (which is currently just using the new disk drive)
Edit /boot/grub/menu.lst and /etc/fstab so that we boot off the new disk and the raid device
Use sfdisk again to copy the partition information from the new drive to the original (I did this because, as it happens, I had changed the partition layout on the new drive after the first sfdiak)
Set-up filesystems on the original disk
Use mdadm --add to add the original drive's partitions to the array[/I]

At no time did I clone partitions between the two drives - I only used sfdisk and cp.

The reason for this post is that, according to blkid, the UUID for /dev/hda1 is the same as that for /dev/hdc1 and /dev/md0.  Similarly the UUID for /dev/hda2 is the same as that for /dev/hdc2 and /dev/md1

It all works fine - and has done so since installation; but reading all this stuff about UUID duplication has made me nervous.

So, are the rules different in a raid1 environment?  Does what I've described look OK to you?

One other point....  In the last few days my swap partition decided to change its UUID (a Feisty feature, from what I understand ;)), but again, that new ID is common to /dev/hda2, /dev/hdc2 and /dev/md1

I had thought about failing one disk in the array, tweaking it's UUIDs and then resyncing, but I thought I'd first ask if these duplicate UUIDs are normal behaviour in a raid1 environment.

Mike

---

### Post by Midahed on 2007-08-17
Anyone got an answer for this?

If you do blkid on a raid1 system, would you expect to see each half of the raid (for instance, hda1 and hdc1) together with the raid device itself (md0) sharing the _same_ UUID as in the example below?

```
root@homepc:/# blkid
/dev/hda1: UUID="bf110005-008d-449b-9ad4-75ed8d66033c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda2: UUID="724baaf7-a07f-42fe-b797-f7e7cb56445f" TYPE="swap" 
/dev/hdc1: UUID="bf110005-008d-449b-9ad4-75ed8d66033c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdc2: UUID="724baaf7-a07f-42fe-b797-f7e7cb56445f" TYPE="swap" 
/dev/md0: UUID="bf110005-008d-449b-9ad4-75ed8d66033c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/md1: UUID="724baaf7-a07f-42fe-b797-f7e7cb56445f" TYPE="swap" 
```

Mike

---

### Post by Midahed on 2007-08-19
Oh well, I can answer my own post now :)

As it happens, I needed to test recovery from my backup, so I made images of each partition on each drive (just in case), erased the entire content of each drive and did a clean install from the alternate cd so that I could build the new raid 1 environment from scratch.

```
root@homepc:/home/mike# blkid
/dev/hda1: UUID="3e890968-b1de-48d7-b842-25f7b85dfcc9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda2: UUID="fd444f02-af56-41e5-beb1-6cf501c648ce" TYPE="swap" 
/dev/hdc1: UUID="3e890968-b1de-48d7-b842-25f7b85dfcc9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hdc2: UUID="fd444f02-af56-41e5-beb1-6cf501c648ce" TYPE="swap" 
/dev/md0: UUID="3e890968-b1de-48d7-b842-25f7b85dfcc9" SEC_TYPE="ext2" TYPE="ext3" 
/dev/md1: UUID="fd444f02-af56-41e5-beb1-6cf501c648ce" TYPE="swap" 
```

As you can see, the UUIDs for the array device itself and for the two component block devices are the same in both cases.

UUIDs appear not to be unique in these particular circumstances.

Mike

---

