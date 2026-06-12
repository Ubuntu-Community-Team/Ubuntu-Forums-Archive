---
title: "Is there a way to scrap Windows in a dual booting system without a format?"
date: 2015-10-12
forum: General Help
---

### Post by aurora4 on 2015-10-12
Hey,
I have an HP laptop that dual boots Windows 7 Ultimate 64 bit and Ubuntu MATE 15.04 64 bit.
I have been able to install Office 2010 on my Ubuntu installation so now Windows 7 is an essential waste of space since I am always on Ubuntu since it's much faster.
I would now like to scrap Windows 7 and make it a Linux only machine. Is there a way to this without a format? It currently has a GRUB menu to boot.
Partition Table:
[TABLE="width: 500"]
[TR]
[TD]Partition[/TD]
[TD]File System[/TD]
[TD]Label[/TD]
[TD]Mount Point[/TD]
[TD]Size[/TD]
[TD]Used[/TD]
[TD]Unused[/TD]
[TD]Flags[/TD]
[/TR]
[TR]
[TD]/dev/sda1[/TD]
[TD]ntfs[/TD]
[TD][/TD]
[TD]System Reserved[/TD]
[TD]100MiB[/TD]
[TD]24.40MiB[/TD]
[TD]75.60Mib[/TD]
[TD]boot[/TD]
[/TR]
[TR]
[TD]/dev/sda2[/TD]
[TD]ntfs[/TD]
[TD][/TD]
[TD]/media/aurora/*bunch of numbers and letters*[/TD]
[TD]111.71GiB[/TD]
[TD]55.34GiB[/TD]
[TD]56.37GiB[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]/dev/sda3[/TD]
[TD]extended[/TD]
[TD][/TD]
[TD][/TD]
[TD]37.24GiB[/TD]
[TD]-[/TD]
[TD]-[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]/dev/sda5[/TD]
[TD]ext4[/TD]
[TD]/[/TD]
[TD][/TD]
[TD]33.33GiB[/TD]
[TD]10.94GiB[/TD]
[TD]22.39GiB[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]/dev/sda6[/TD]
[TD]linux-swap[/TD]
[TD][/TD]
[TD][/TD]
[TD]3.90GiB[/TD]
[TD]69.54MiB[/TD]
[TD]3.84GiB[/TD]
[TD][/TD]
[/TR]
[/TABLE]

/dev/sda2 is the partition where there's Windows

Thanks,
Aurora

---

### Post by sudodus on 2015-10-12
Welcome to the Ubuntu Forums :-)

***Please think twice before removing Windows!*** In the future you may need be some program or peripheral device, that needs Windows. Make a complete ***backup*** or at least create ***recovery disks*** for Windows, so that you can get it back, if you change your mind.

Anyway, the answer is ***yes***. It is enough to remove all the files in the Windows partition. Then you can use that partition as a data partition (to store various data files). But it might be worthwhile to use ***gparted*** to create a linux file system (for example ext4) in the previous Windows partition if you have only linux in the computer, because it works faster and better with linux. And then you do it 'with a format' ;-)

If you want to get rid of the 'Windows line' in grub you run the following command (after you have removed all the files in the Windows partition).

```
sudo update-grub
```

---

### Post by ian-weisser on 2015-10-12
+1 to Sudodus' advice. Deleting Windows is easy to do, a bit painful to undo.
I deleted Windows 10 years ago at home, but still need the occasional Windows application at work.

You have two alternatives to delete windows.

1) You can scrap Windows today by using a partitioning tool (like parted or gparted) to erase (format) the ntfs partition #2 to ext. Then, typically, you would use that big empty partition for your personal data (/home) by editing your /etc/fstab. This is the preferred way if you love to tinker and learn about how your system works. Backup your data before tinkering with your /home - you might accidentally make all your personal data inaccessible.

2) Since you are running 15.04, which will EOL in January 2016, you must upgrade to 15.10 soon anyway. So another option is to backup your data and completely reinstall using a 15.10 LiveUSB (after 15.10 is released). The installer will repartition your entire hard drive (which is why you backed up your data). This is the preferred way if you dislike tinkering and want it to just work.

---

### Post by yancek on 2015-10-12
Another option since your windows system partition is only half full, boot windows 7 and go to Disk Management and shrink that partition.  You will then have unallocated space on which to create a Linux partition/filesystem to be used for data with Ubuntu.

---

### Post by lisati on 2015-10-12
+1 to the other suggestions.

Whatever you decide, whether it's resizing Windows, deleting Windows completely, or something else, be sure to make backups and recovery disks. It can be really frustrating when you have made changes to your system and later discover that you've deleted or broken something you need later.

---

### Post by tristan16 on 2015-10-12
Can I just ask you guys something? Why is it that on **Ubuntu **forums, you always tell people to keep *Windows?* You make it seem like it's impossible to completely switch. Sure, I still have Windows installed, but I never use it because I found Ubuntu alternatives for all my software.

---

### Post by ian-weisser on 2015-10-12
> **tristan16 said:**
> Can I just ask you guys something? Why is it that on **Ubuntu **forums, you always tell people to keep *Windows?* You make it seem like it's impossible to completely switch. Sure, I still have Windows installed, but I never use it because I found Ubuntu alternatives for all my software.

Really a separate topic, worthy of it's own thread.

We don't *always* tell people to keep windows. We try to give safe advice for what little we know about the user's situation.
For some users, especially experienced Windows users starting to experiment with Ubuntu, it's a good idea to keep Windows a bit longer. That user group is strongly represented among the help threads - it's the new users who need the help.
We have many threads here of a new experimenter who, horrified, realizes too late that they still need Windows for their favorite game or school-critical application or vendor-locked business data.

I have been completely switched at home for a decade. It was the right answer *for me*. Since I don't know the right answer for anyone else, I stick to safe answers.

---

### Post by SantaFe on 2015-10-12
Because there's always that one time you might Need windows to do something.  Like updating your bios for one.  Most all the BIOS updater programs I've seen only run under windows.  Of course now that I've said this I noticed this in Synaptic.

firmware-addon-dell: The firmware-addon-dell package provides plugins to firmware-tools which enable BIOS updates for Dell system, plus pulls in standard inventory modules applicable to most Dell systems.  

Besides, Windows isn't our enemy after all, just a different O/S.  And from the latest news, Microsoft is discovering it needs Linux as well. ;)

---

### Post by aurora4 on 2015-10-23
Thanks for all the replies but I went with installing Ubuntu MATE 15.10 yesterday :)
I forgot to reply sorry >.<
Thanks,
Aurora

---

