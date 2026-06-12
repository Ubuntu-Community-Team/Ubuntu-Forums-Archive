---
title: "slow-mounting pendrive issue (unison related?)"
date: 2013-08-23
forum: General Help
---

### Post by henkeldg on 2013-08-23
Greetings fellow Ubuntians,

I've been experiencing a problem with a USB drive that I've never encountered before and that I can't find anywhere in any forums. My system is Xubuntu 13.04 64-bit, with / and /home on separate partitions, using either XFCE or LXDE as my desktop environment. My computer double-boots Windows 8 although I rarely use it. I have a 16GB Kingston pendrive that I use essentially for backup with Unison. It's formatted with a 512MB FAT partition and a 15GB Ext4 partition. The problem is as follows :

1/Pendrive used to be instantly recognized and mounted
2/For several days following a failed Unison sync, the drive has been taking 4-5 minutes to be recognized and mounted both with XFCE and LXDE
3/I have other similar USB drives which are instantly recognized and mounted
4/When the same drive is connected to the same machine running Windows 8 the 512MB partition shows up immediately
5/When the same drive is connected to other machines running Ubuntu 12.04 both partitions show up instantly
6/I have re-installed Ubuntu and reformatted the drive, yet the problem persists

Basically, there seems to be a communication issue between my machine and this one drive. Although this could be coincidental, the problem seems to have started after I mistakenly ran Unison with a different pendrive in the USB slot and received an error message to the effect that it couldn't find the one that Unison was looking for, which now is slow to be recognized and mounted. It seems as if somewhere in the hidden configuration files in my home folder this drive has now been identified as problematic, when in fact it works perfectly.

Has anyone ever encountered a problem like this, or can anyone suggest a fix?

Best regards,
DGH

---

### Post by sudodus on 2013-08-23
I use ***Unison*** and I don't think the mistake you made with the wrong pendrive would destroy mounting the right one.

If you have reinstalled Ubuntu and reformatted the pendrive, there should be no memory of the history in the software. Did you reformat also the home partition? If not, you can try to mount the pendrive from another user ID.

Have you tried to mount a partition on the pendrive using the terminal window command ***mount***?

```
 sudo mount -t auto /dev/sdxy /mnt
```

where x is the drive letter and y is the partition number, *edit*: typically /dev/sdb2 for drive b, partition 2.

Otherwise, only hardware alternatives remain: There is something fishy with the pendrive or the USB system or a single USB port on the computer.

---

### Post by henkeldg on 2013-08-23
I don't see how it can be a hardware issue, the pendrive shows up immedately on other computers, and other pendrives show up immediately on my laptop, it's a communication issue between my laptop and this particular pendrive. Update: the pendrive shows up immediately on my laptop as before when running a live session of Xubuntu 13.04 off another USB drive, so it has to be something somewhere on the internal hard drive. No, I haven't reformatted my /home partition yet, I'd like to avoid that option if at all possible (it's the whole reason why I have a separate /home partition). I don't know anything about UEFI, but I've had to leave the UEFI sector on the disk in order to double-boot Windows 8, and I'm wondering if there might be some record of my USB drive there?

---

### Post by sudodus on 2013-08-23
I see. You could make a (temporary) new user, and see if that user can mount the pendrive.

You can also try to mount it with sudo mount (which means that the user 'root' will be mounting it without interference of your current user. At least sudo -i should be 'clean'

```
 sudo -i mount -t auto /dev/sdxy /mnt
```

I have been told that Windows writes into the UEFI partition, but I don't think Ubuntu does it (except maybe during the installation).

Do you have an entry for the pendrive in your [FONT=courier new]**/etc/fstab**[/FONT] file? Do you mount it with your file browser, or do you automount it when connected?

---

### Post by henkeldg on 2013-08-23
There's nothing in fstab.d, and mount answers "mount: special device /dev/sdb2 does not exist", but if I wait long enough (3-5 min) it shows up in the file manager, and then can be mounted either with the terminal command you suggested, or simply by clicking on it in the file manager.
As for EFI, I'm not really sure what goes on there, but I think Ubuntu must communicate with it somehow because that's where GRUB2 is written when you set up the double boot with Windows. I'll try making a new user to see if the drive can be accessed more quickly from a new account.

---

### Post by henkeldg on 2013-08-23
OK, I tried it out on the guest account. Also I tried this experiment: I formatted another USB drive with 2 partitions, FAT and EXT4, like the one I've been having problems with. In the guest account, the new one shows up immediately with both partitions, the old one remains invisible. Both drives show up immediately with their separate partitions in another computer running 12.04 LTS. It occurred to me that it might be the most recent update to 13.04 that was causing trouble when opening drives with multiple file systems, but that doesn't seem to be the case.

---

### Post by sudodus on 2013-08-24
You tested a lot of alternatives and ruled out quite a few possible causes :-)

I must admit, that I don't understand what is wrong. It seems that one computer and one pendrive have problems talking to each other. The computer has no problems with other pendrives and the pendrive has no problems with other computers.

I don't know if and how pendrives (or in general: mass storage devices) can be blacklisted. It is more likely (to me) that there is a regression due to an update in 13.04, and that there is something fishy with that particular pendrive.

You could try to wipe the first megabyte of the pendrive with zeroes, and then make a new partition table and file systems.

Use ***dd*** according to this link to wipe the first megabyte: [Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073"). 

Use ***gparted*** to make a new partition table and file systems

---

### Post by soyos on 2013-08-25
[COLOR=#323D4F][FONT=Lucida Grande]Hi![/FONT][/COLOR]

[COLOR=#323D4F][FONT=Lucida Grande]I have had similar problem. [/FONT][/COLOR][COLOR=#323D4F][FONT=Lucida Grande]My laptop (TOSHIBA Satellite L30 Version: PSL33E-03L03PHU)[/FONT][/COLOR][COLOR=#323D4F][FONT=Lucida Grande] works with the 3.8.0.23.39 kernel, but don't work with the new 3.8.0.29.47. [/FONT][/COLOR]
[COLOR=#323D4F][FONT=Lucida Grande]
 It has that chipset:[/FONT][/COLOR]

[COLOR=#323D4F][FONT=Lucida Grande]"00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI IXP SB400 USB Host Controller (rev 80)"[/FONT][/COLOR]
[COLOR=#323D4F][FONT=Lucida Grande]
I switched back to [/FONT][/COLOR][COLOR=#323D4F][FONT=Lucida Grande]3.8.0.23.39 [/FONT][/COLOR][COLOR=#323D4F][FONT=Lucida Grande]kernel[/FONT][/COLOR][COLOR=#323D4F][FONT=Lucida Grande]... [/FONT][/COLOR][COLOR=#323D4F][FONT=Lucida Grande]

Kind regards, Zoltan[/FONT][/COLOR]

---

### Post by henkeldg on 2013-08-25
Well, that summarizes it pretty well: one computer (coincidentally, the only one I have running 13.04) having trouble communicating with one particular USB pendrive. I think we can safely say this is a regression in 13.04 concerning one particular model of USB drive which I happen to own (a 16GB Kingston DT101 G2). Here's how I arrived at this conclusion:

1/There's no problem recognizing and mounting the drive on other computers running 12.04
2/No problem mounting the aforementioned drive during a live session of 13.04 on my laptop (running off a live USB drive made from the .iso of 13.04, presumably without updates)
3/No problem mounting the said drive on my laptop after wiping the disk completely and a clean re-install of 13.04
4/No problem mounting the drive on my laptop after a reboot of 13.04 before installing updates
5/AFTER installing the most recent updates of 13.04 on my laptop, I have to wait around 5 min. for the drive to show up
6/Other drives and SD cards, however, even formatted with multiple file systems, show up immediately on my laptop running the latest updated version of 13.04, so it would seem it's just my rotten luck that this one drive is affected by what appears to be a regression.

---

### Post by soyos on 2013-08-25
Well, I agree. You could install every update, except kernel update. It works for me...

Kind regards, Zoltan

---

### Post by sudodus on 2013-08-26
> **soyos said:**
> Well, I agree. You could install every update, except kernel update. It works for me...

Kind regards, Zoltan

+1

---

### Post by soyos on 2013-08-27
[https://bugs.launchpad.net/ubuntu/+s...g/+bug/1207934]("https://bugs.launchpad.net/ubuntu/+source/linux-lts-raring/+bug/1207934")
Here is the bug report.

---

### Post by henkeldg on 2013-08-27
Thanks, Soyos. I was wondering whether I should submit a bug report, or whether the problem was too eccentric to bother with.

---

### Post by henkeldg on 2013-09-06
After the most recent updates, the drive is back to its old speedy self. Just a temporary, albeit initially baffling, regression.

---

### Post by sudodus on 2013-09-06
I'm glad your system is OK again :-)

---

