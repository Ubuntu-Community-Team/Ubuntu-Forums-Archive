---
title: "Bad power supply, then can't boot. Floppy disk error!!"
date: 2018-10-06
forum: General Help
---

### Post by 1clue on 2018-10-06
Hi,

I have an older system running Ubuntu. It's an i7 920 on an Asus P6T motherboard, I think circa 2011 or so. 24GiB RAM, 1x SSD, 4x hdd. 2 of those are in RAID.  NO FLOPPY! It's in a mini tower.

This is my development box right now, and it's how I make my living.

Over the past couple weeks I noticed my mouse acting up. It would sporadically stop working, then after some percussive maintenance it would start up again. I finally looked at it, and the LED flickers on and off so it's a bad cable or something. Replaced the mouse with a new one. That one simply didn't work at all. Then the keyboard acted up, replaced it with another I had laying around.  Everything is USB, no wireless anything.

The "new" keyboard has a sleep button very close to the escape key. I don't normally sleep it, and I accidentally hit that and it went to sleep.

I could not get it to wake up.

[LIST]
[*]I hit the reset button 
[*]I powered the system off and then on 
[*]I cycled the switch on the power supply. 
[*]I checked that the power cord has power to the power supply (yes) 
[*]I disconnected the power supply and connected the green wire to first one adjacent black wire, then the other adjacent black wire. The fan did not come on. 
[*]I bought a new power supply, which happens to be the same brand and rating as the old one. A little bit newer as there are more SATA connectors on this one. 
[*]The system powers up but does not boot. It goes past the BIOS screens, gets to grub and no matter what option is taken it does the same thing (see below) 
[*]I booted from system rescue cd, fsck and it cleared a lot of inodes on my root filesystem. So it had filesystem damage. 
[*]I tried booting again several different ways. 
[*]I booted from system rescue cd, mounted my key partitions using the /etc/fstab as a guide, reinstalled grub, grub-mkconfig -o /boot/grub/grub.cfg 
[*]Same results as below. 
[/LIST]

This is typed on another computer while watching the screen of the problem system. Time stamps are not accurate, and there may be misspellings in there.

```

[   87.188973]Running /scripts/local-premount ... print_req_error : I/O error, dev fd0, sector 0
[   87.189381]floppy: error 10 while reading block 0
[   87.219225]print_req_error: I/O error, dev fd0, sector 0

```

It goes on like that forever, every few seconds adding a new pair of lines, the last 2 of the code snippet.

I'll say again this system does not have a floppy. Has never had a floppy. None of the systems I have managed since this was a new box have had floppies. I'm a bit confused as to why power supplies still have a floppy connector, nobody has floppies. It does have /dev/fd0 of course, and I did not try to remove the file. I've been a Linux user and admin for decades, I know how device files work. My Gentoo systems don't have floppy support built into the kernel.

Some of the SATA cables came off during the power supply replacement. I did my best to get them back on, but I don't think that's really it because /etc/fstab uses UUID for / and /boot, and everything else is on lvm2 and is mapped through /dev/mapper. The UUIDs have been checked and they match to the one I want.

About the only thing I haven't tried is a reinstall. I don't particularly want to do a reinstall, because this is a dev box and there has been a bit of not-in-the-repo code done here. Much of it coded by me. I'd rather not go through the hassle of reinstalling all that.

**The question: Can anyone think of something else to try, except the reinstall?**

If not, then I'll back up my /etc, /usr/local, /opt and whatever else I can think of, and reinstall without formatting. That wipes the directories installed by Ubuntu, which will wipe much of my customizations too, but it's all I can think of to get the system back.

---

### Post by TheFu on 2018-10-07
Ouch.

Motherboards do wear out, eventually.  Id pull the disk out and put it into a different machine. See if that solves it. My i7-920 is from 2009, BTW.  Ive been looking to replace it and another machine with a ryzen 2600. Now that RAM prices are finally dropping.

Ive seen a flaky GPU cause strange problems. Only with addon GPUs, never iGPUs.  

BTW, the least 2+ weeks, my mouse has been acting funny too. It was moving on its own, but always towards the right of the screen. Replaced it which seemed to fix the issue, until yesterday.  Now the mouse seems to select text in the active terminal without me touching any buttons.  My main desktop runs inside a VM and is accessed via x2go over a network connection.  I think my KVM might be failing.  It is almost 15 yrs old and uses PS2 connections, not USB.

After checking all the connections, trying it in a different machine, I really dont have any other suggestions.

You know this already, but if your backups arent daily, automatic, versioned, and can restore the system to working in 30-45min (minus any huge data), they definitely need to be improved.

---

### Post by 1clue on 2018-10-07
This is at home, and I don't have another appropriate box I can test with. And 2009 is possibly correct. The chip had just came out, so that's probably it.

It has an add-on GPU. Never had problems with that before, but it's an old box.

It's odd that you're experiencing similar problems in the same time frame. That suggests something else, but the fact of your having the same chip is interesting. My mouse behavior was just it sporadically not working, the way that a dirty mouse acted back when they had balls in them.

Yes I know about and have backups. I've posted mind-numbing details of my opinions about backups before, and I'm pretty sure you've been seen on the same threads. The critical aspects of this system are backed up, but there are 2 points:
[LIST=1]
[*]This is a dev box and my workstation. All my source is on git of course, but I don't back up binary apps so I'll have to rebuild the system. But there are script tweaks all over, and it might be a bit of a pain to collect all that. Especially if one of them is corrupt. 
[*]Since this is the weekend I thought I might try to actually debug this one through, rather than just blast over the top of it.  But I'm getting to that point where I need to get it working again. 
[/LIST]

You've pretty much told me what I need to know, so rebuild/restore it is.

Thanks

---

### Post by TheFu on 2018-10-07
So, I think I figured the issue out.  I hadn't rebooted since patching.  Reboot fixed it for me. Yesterday, about 5 more keys stopped working. Because some keys had been broken for months, I assumed 5 more just ran out of time and that was it.  Reboot.  All those keys started working again, well, except the R-arrow is still not working great.  

On my desktop, the setup isn't exactly normal.  It runs inside a VM with x2go for access. Can't remember the last time the console was used on that physical machine.  It runs 14.04 for the VM host. It has 1 Win7 VM on it that probably will be a pain to move up.  It was last time going from 10.04 --> 14.04.  All the Linux VMs move easily, basically without any thought necessary.

You can't try swapping the disk into another PC?  Maybe a used $90 Core i5 would be sufficient for that from the lease return at Microcenter?

---

### Post by Yellow Pasque on 2018-10-07
You do have the floppy controller disabled in the BIOS, correct? From the manual, it looks like this setting is called "Legacy Diskette A" in the BIOS.

---

### Post by 1clue on 2018-10-09
Sorry I posted an answer yesterday and it didn't show up!

@Temüjin: Yes the floppy is disabled in the bios.

@everyone:

On Sunday I pulled the plug on my research and reinstalled the OS. I have everything backed up, but I never back up binaries. I had hoped to learn something this last weekend with respect to repairing a broken system, but really it was the same old thing.

I had lots of inodes cleared when I booted off the system rescue CD and did an fsck on /. It's my opinion that it was trashed due to the bad power supply, maybe the wrong voltage causing the problems.

On researching what was on the drive, I decided that I needed a fresh start. The /usr partition was 12G all by itself, which is ridiculous. There was a ton of stuff on there that I either looked at once and forgot about, or that was superseded by something else and never removed.

The new install fits in 10G for the / partition, with /usr included in that. I have all my sources and work stuff mostly on separate filesystems, and I'm going through that to see really what needs to be kept and what can be wiped. I've been slamming restored data back into upgrades and installs for so long there is stuff in there (my data) that's more than 10 years old. So it's time for housekeeping.

---

### Post by 1clue on 2018-10-09
What's odd now is that the system fans are running fast. Temperatures are low, so I'm not sure what's going on there. I never had to mess with this stuff before, it always just worked. And I was already on 18.04, but it was an upgrade rather than a fresh install.

hardinfo shows it's a single fan running fast, around 1400 rpm. The next fastest is 800 rpm, which is what I remember them all running at before.

---

### Post by 1clue on 2018-10-17
OK so here's the deal.

I've been running this setup ever since this problem started, by not mounting a separate /usr. My /usr was on LVM2, but with the reinstalled OS it was all just on my 10GiB / partition.

Today I ran out of space on /, so my first thought (and action) was to:

 ```
mount /dev/ssdvg1/host_usr /mnt
rm -rf /mnt/*
cp -rax /usr/* /mnt/
vim /etc/fstab (and add an entry for /usr)
mv /usr /usr.old
mkdir /usr
mount /usr
diff -r /usr /usr.old
reboot

```

So my messages came back. This time I knew the only substantive difference was that /usr was on a separate filesystem, and it was on LVM2.

I'm figuring my initrd is messed up, doesn't do lvmetad.

While I was booted on system rescue cd I found a bug on ubuntu's database, now I can't find it. It was talking about a solution posted in initramfs-tools-0.130ubuntu10. I couldn't figure out how to install that from a chroot in sysrcd but I reversed my /usr deal, deleted everything I could find on / that I didn't need, and commented out the /etc/fstab /usr entry. Reboot.

Got my system back, couldn't find the one about initramfs-tools but I found this one instead: [https://askubuntu.com/questions/745218/ubuntu-wont-boot-because-of-lvmetad#752282](https://askubuntu.com/questions/745218/ubuntu-wont-boot-because-of-lvmetad#752282)

I followed the instructions and re-did my /usr fstab entry, drained the root volume /usr again and rebooted. It took about an extra 45 seconds to boot, but it boots.


So now I gotta figure out how to have one package and critical dependencies in unstable and everything else stable.

---

