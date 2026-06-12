---
title: "Ubuntu 20.04 live usb ruined one of my hard drives"
date: 2020-06-06
forum: General Help
---

### Post by rob444 on 2020-06-06
I currently have Windows 10 installed on my computer with several hard drives as storage medias.

I downloaded and made a bootable USB out of Ubuntu 20.04. I ran the live USB without installing anything.
While inside I just installed the Nvidia drivers through Software center or whatever it's called. Software center (or whatever it's called - again) wanted me to update so I tried it and then it wanted me to reboot, which I of course didn't since I'm running it live from an USB.
After that I tried to install Wine with no success.

I accessed my system drive which has NTFS as a file system and some other drives (storage medias) that has the same file system and nothing else.
I power off my machine through Ubuntu and boot back into Windows.
One of my hard drives is no longer recognized by Windows. It's considered to be in "RAW" format. I tried to use chkdsk to recover but it says my NTFS boot record is corrupted.
Why is this? I didn't even use commands that are remotely near disk manipulation unless the software update did something...

The disk is there but there is no partition data. I'm currently running some software that scans my hard drive after lost partition data and it takes many hours to scan a 2 TB hard drive so it's not completed yet.
It has found after 60-ish percent that there is a file system "Ext4" of 7 gb of size. 3.19 gb is being used. Why is this?

I'd appreciate some help here on how to remove that ext4 and whatever data it holds and let me fix the NTFS records so I can access the 2 TB of data of backups throughout my life. :cry:
Why did a live version alter my hard drives to begin with?

---

### Post by ActionParsnip on 2020-06-06
You must have formated a partition. The liveCD/USB OS doesn't modify disks on its own.

---

### Post by ActionParsnip on 2020-06-06
Why not just wipe the partition off, make a new NTFS partition and restore your data from your backups... You do have backups.... Right?

---

### Post by rob444 on 2020-06-06
> **ActionParsnip said:**
> You must have formated a partition. The liveCD/USB OS doesn't modify disks on its own.

It shouldn't but something did which is weird.  I did not run any commands as far as I know that alters drives.

---

### Post by rob444 on 2020-06-06
> **ActionParsnip said:**
> Why not just wipe the partition off, make a new NTFS partition and restore your data from your backups... You do have backups.... Right?

We all do have backups of some sort. These drives I have are backups and I did not expect a live usb version of Ubuntu to alter them. So don't try to blame me for having a "bad" backup.

---

### Post by GhX6GZMB on 2020-06-06
There's no way a live disk can do this. The only way is for you to run some command using sudo privileges with password "Ubuntu". 'Fess up.

---

### Post by kneutron on 2020-06-06
> [COLOR=#000000]I accessed my system drive which has NTFS as a file system and some other drives (storage medias) that has the same file system and nothing else

--It sounds like if you didn't mount the NTFS partition as read-only, it might have altered something.  

> [/COLOR][COLOR=#000000]It has found after 60-ish percent that there is a file system "Ext4" of 7 gb of size. 3.19 gb is being used

--And that sounds like you tried to "install ubuntu" to that partition.  Something tells me we don't have the whole story here, and I'm finding it hard to place blame on the live usb.[/COLOR]

---

### Post by rob444 on 2020-06-06
> **kneutron said:**
> > [COLOR=#000000]I accessed my system drive which has NTFS as a file system and some other drives (storage medias) that has the same file system and nothing else

--It sounds like if you didn't mount the NTFS partition as read-only, it might have altered something.  

> [/COLOR][COLOR=#000000]It has found after 60-ish percent that there is a file system "Ext4" of 7 gb of size. 3.19 gb is being used

--And that sounds like you tried to "install ubuntu" to that partition.  Something tells me we don't have the whole story here, and I'm finding it hard to place blame on the live usb.[/COLOR]

But ***it is*** the whole story.

I did not try to "install" ubuntu. I just wanted to try out the performance with Nvidia drivers. I was only running live for like 5-10 minutes and then I had to boot back to Windows to answer a gazillion questions over facebook messenger.
Maybe my drive decided to  die just now even though SMART results gives me an okay? I might add this is not the first time a computer decided to screw with me after using Ubuntu :p
It pixelated my new laptop once and after that (killing pixels), it left my built-in network card in a certain state that not even a reboot or power off worked.
Not saying Ubuntu is bad, I really want to use it but it seems it has a way of killing things...

---

### Post by rob444 on 2020-06-06
Funny how third party software found around three EXT4 partitions on the disk that I never touched.

---

### Post by dragonfly41 on 2020-06-07
[COLOR=#000000]> so I can access the 2 TB of data of backups throughout my life. 

This is just a tip from hard learned experience. *Do not keep you life's work in a single potential point of failure*. Keep multiple backups using n redundancy principles. Here endeth the lesson.

Now if the LiveUSB was persistent (I guess it is not) you could have run terminal history command to give a list of commands you had run, as an audit trail. Otherwise we are left guessing what actually happened.

Often drives which seem unrecoverable can be recovered after calmly thinking through the next steps. If your entire life's work is indeed in a single 2TB device I would go out and purchase two (yes two) similar size devices with USB containers for each one.   I use an external dual docking bay for convenience. Manufacturer StarTech UNIDOCKU33.  Then I would clone your problem drive into one of the two external drives.  ddrescue will do this.  Then start trying to recover the *cloned *image keeping the original untouched in reserve.  The third drive will be required if you reach a point where you have to use some utility like testdisk to recover files from your cloned drive since you will need somewhere to place them.

My policy now is to leave Windows 10 drive untouched although I still have an old Ubuntu installation in there. Ubuntu in a second (external USB SSD). Two additional drives (now SSD's) one for backup and the other in reserve. This is a hit on your pocket money but gives the tools for recovery.  Follow the advice of others here on regular backup strategy to follow such as using Timeshift (there are multiple backup approaches well documented in this forum).[/COLOR]

---

### Post by rob444 on 2020-06-07
> **dragonfly41 said:**
> [COLOR=#000000]

This is just a tip from hard learned experience. *Do not keep you life's work in a single potential point of failure*. Keep multiple backups using n redundancy principles. Here endeth the lesson.

Now if the LiveUSB was persistent (I guess it is not) you could have run terminal history command to give a list of commands you had run, as an audit trail. Otherwise we are left guessing what actually happened.

Often drives which seem unrecoverable can be recovered after calmly thinking through the next steps. If your entire life's work is indeed in a single 2TB device I would go out and purchase two (yes two) similar size devices with USB containers for each one.   I use an external dual docking bay for convenience. Manufacturer StarTech UNIDOCKU33.  Then I would clone your problem drive into one of the two external drives.  ddrescue will do this.  Then start trying to recover the *cloned *image keeping the original untouched in reserve.  The third drive will be required if you reach a point where you have to use some utility like testdisk to recover files from your cloned drive since you will need somewhere to place them.

My policy now is to leave Windows 10 drive untouched although I still have an old Ubuntu installation in there. Ubuntu in a second (external USB SSD). Two additional drives (now SSD's) one for backup and the other in reserve. This is a hit on your pocket money but gives the tools for recovery.  Follow the advice of others here on regular backup strategy to follow such as using Timeshift (there are multiple backup approaches well documented in this forum).[/COLOR]

The usb drive was not persistent so no terminal history but the only terminal commands I used was apt and try to get down wine through apt, nothing else.
Yeah, I've learned a lesson. I usually buy new drives and just clone the old ones to the new ones. There doesn't seem to be anything wrong with the actual disk, all signs points toward good condition (SMART, sector scanning etc.).
I ordered two 4 TB drives now. I'm going to buy an external USB backup drive as you mentioned, it's a really good advice.
I'm doing one last attempt to scan for lost partitions, after that I should just wait for the drives and then try to recover as much as possible. Thanks for the advice!

---

### Post by dragonfly41 on 2020-06-07
There is one thing you might try. Using LiveUSB launch GPart Partition Editor and scan your drives.
In GParted menu bar there is an option .. Device > Attempts Data Rescue. You could try that on the cobbled drive. I can't remember if gparted is there by default with a LiveUSB but if not it can be installed.

On the matter of using external USB SSD/HDD if you can use USB 3.0 port so much the better for performance. Read the [notes published by StarTech]("https://www.startech.com/uk/UNIDOCKU33") on  this.  I am writing this note on an external Ubuntu USB/SSD via USB 3.0 and it is so much faster than the resident Windows 10 resident in the internal HDD in my host Dell.

---

