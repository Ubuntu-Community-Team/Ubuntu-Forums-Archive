---
title: "A Problem in the BOOT"
date: 2006-07-22
forum: General Help
---

### Post by mllr on 2006-07-22
Hello guys!
Before I explain the problem, note that I'm brazilian, and English isn't my Mother-Language, so, you may see some problems on my english...

Guys, the problem is this: I have two HD's in my computer, one Maxtor IDE 40GB and one Seagate SATA 80GB. When I was initializing with linux, I installed ubuntu (and some other distros before) in the "secundary" HD, the Maxtor ones, and Windows still installed in the SATA ones...

After one month using Ubuntu, yesterday I decided to put linux in the "principal" HD, the seagate ones... So, I put all the important data of the Seagate HD to the Maxtor HD, and formated, installed, customized all the ubuntu in the Seagate HD...

It was yesterday... I went to sleep, with no problems...

I woke up today, initialized the computer and OMG! The BIOS was giving me +- this message:

```
Insert a boot media and press enter
```

Me: "Ok, ok... one common bug, lets reboot..." And the problem persists...

Soo, I booted with the Ubuntu Live-cd and asked to my friends about the problem... I searched much things about it and looked that the BIOS wasnt checking the IDE-HD... Ok, we have a problem with the IDE-HD, ok? But WTF the SATA wasnt running? So, i got and idea...

When I installed ubuntu in the SATA, I was booting it at the IDE, and using the GRUB for the SATA... And Ubuntu (i dunno why) didn't install the Grub in the Sata! So, i went to the packages.ubuntu.com, downloaded the grub-disk, installed it in the ubuntu running in the livecd and burned the iso in a CD-RW and booted it... Opened the grub and havent the option to boot on "ubuntu", so, i enter the option to install grub in the HD, and voilà, i got the old list of ubuntu, with options to load in the IDE and SATA, but it was configured to load IDE how the first HD... ok ok, i booted with the livecd again, mounted the SATA HD and changed the options in the grub config file, booted from de HD, and, yeees, it was running!

So, when the ubuntu was loading, I got this error:
```
Reloading Postfix Configuration		[failed]
```

it stopped for some seconds and enter in the Text Mode, where i could see this error message:

```
Checking Filesystems
fsck.ext: No such file or directory while trying to open /dev/hda1
/dev/hda1:
The superblock could not be read or dows not describe a correct ext2 filesystem. If the device is valid and ir really contains a ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt, ant you might try running e2fsck with an alternative superblock:
e2fsck -b 8193 <device>
```

And I'm here know cuz' I used "startx" but im using it without my configurations, as the root...

And here is my request:
- For the comunity: what can I do to resolve the problem?
- For the staff: Why Ubuntu installed in one HD, needing the another? Why it didn't installed the "ubuntu full"?
- And finally (and off-topic) for those that know something about hardware, what can I do to a diagnostic about my IDE HD?

Thank you guys!

---

### Post by steve.horsley on 2006-07-22
> - For the comunity: what can I do to resolve the problem?
- For the staff: Why Ubuntu installed in one HD, needing the another? Why it didn't installed the "ubuntu full"?
- And finally (and off-topic) for those that know something about hardware, what can I do to a diagnostic about my IDE HD?
I can provide a partial answer to the middle one. 
On an IDE machine, Linux sees  hda and hdb etc. Grub sees them as (hd0) and (hd1).
On a SATA machine, Linux sees sda and sdb, grub sees (hd0) and (hd1). 
On a mixed machine, Linux sees hda and sda. What does grub see?

I think there may be problems in the grub installer converting the Linux names to grub names. That's as far as my understanding goes. There's a file /boot/grub/device.map that might help.

---

### Post by zxee on 2006-07-22
> And finally (and off-topic) for those that know something about hardware, what can I do to a diagnostic about my IDE HD?

Do a search on smart. I believe it may be available through apt. (I'm not on my home computer right now)
Here's one link which provides a bootable floppy image to check scsi and ide drives: [http://www.hitachigst.com/hdd/support/download.htm](http://www.hitachigst.com/hdd/support/download.htm)

---

### Post by Ocxic on 2006-07-22
you have the exact same prblem that i did, i find that IDE and SATA drives conflict with grub, the solution for me was to make a small boot partition (200MB) on my IDE drive and set the as the first drive in my bios and installed grub there, scince then I've had no problems. 

just install grub to your IDE drive, set as master in bios, and you should be good.

---

### Post by mllr on 2006-07-22
> **steve.horsley said:**
> I can provide a partial answer to the middle one. 
On an IDE machine, Linux sees  hda and hdb etc. Grub sees them as (hd0) and (hd1).
On a SATA machine, Linux sees sda and sdb, grub sees (hd0) and (hd1). 
On a mixed machine, Linux sees hda and sda. What does grub see?

I think there may be problems in the grub installer converting the Linux names to grub names. That's as far as my understanding goes. There's a file /boot/grub/device/map that might help.

Yeah, I saw that when I was repairing the problems in the GRUB, and all the problems with the GRB are solved, thank god!

BTW, I wouldn't have this problem if the ubuntu live-cd installed the grub in the SATA HD, do you understand me?

> **zxee said:**
> Do a search on smart. I believe it may be available through apt. (I'm not on my home computer right now)
Here's one link which provides a bootable floppy image to check scsi and ide drives: [http://www.hitachigst.com/hdd/support/download.htm](http://www.hitachigst.com/hdd/support/download.htm)

Thank you, I'll do the Hitachi's test, and after you tell me about diubg a search on smart (I really didn't understand the menaing of it) =)

> **Ocxic said:**
> you have the exact same prblem that i did, i find that IDE and SATA drives conflict with grub, the solution for me was to make a small boot partition (200MB) on my IDE drive and set the as the first drive in my bios and installed grub there, scince then I've had no problems. 

just install grub to your IDE drive, set as master in bios, and you should be good.
Yeah, but I don't want two ubuntus in two drives... I was transfering ubuntu from one to another drive, and the IDE would be a Sotorage for me, did u understand?

Guys, about the problem in the BOOT, I solved it removing the hda's entries in the fstab, but I still needing help about the diagnostic on the HD...

If a Moderator think that's better to move the topic from here to another section, do it please.

---

### Post by mllr on 2006-07-23
zxee

the hitachi test didnt find the IDE drive...

the BIOS can't find it too =(

any ideas?

[]'s

---

