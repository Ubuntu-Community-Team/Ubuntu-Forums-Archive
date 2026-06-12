---
title: "Does the NTFS-3G driver still use a lot of CPU resources to write to NTFS?"
date: 2012-11-05
forum: General Help
---

### Post by mikodo on 2012-11-05
Hello,

I am thinking of downloading binaries from usenet in Xubuntu and saving them in a NTFS linux /media mounted data partition and sharing it in a Windows mounted drive, in a home wired connection (not network), for my wife.

[From this Link]("http://superuser.com/questions/100629/whats-the-best-way-to-share-files-between-linux-and-windows-7-on-a-dual-multi-b"), is the following still true, about the large CPU resources the NTFS-3G driver uses, to do this?

Quote:

[LEFT][COLOR=#000000][FONT=Arial]*"I did not want to use NTFS, because the native Linux support for it isn't complete (writing is not fully supported) and the NTFS-3G driver uses too many resources - downloading a file from the Internet with a 100Mbit connection almost freezes my Core i3.*[/FONT][/COLOR]"
[/LEFT]
 
End Quote.

[Wikipedia link]("http://en.wikipedia.org/wiki/NTFS-3G")

Quote:[I]

Performance:[/I]

[I] "Current versions often show 100% CPU utilization on dealing with big files on fragmented NTFS file systems."

[/I]End Quote.

Edit:

Maybe I should be looking at using:

[Samba]("https://help.ubuntu.com/community/Samba")   (doesn't seem easy though)

[FTP and Zeroconfig]("https://help.ubuntu.com/community/EasyHomeFileSharingWithFTPAndZeroconf")  (might be easier to use)

Thanks.

---

### Post by mikodo on 2012-11-05
Oh, the heck with it. Everything I read about seems too difficult/not suitable. If she wants to access my files, then I am going to only offer to make them available to a 'buntu/linux system.

Thanks.

---

### Post by mastablasta on 2012-11-05
samba might be already preinstalled. if not install it, set a folder that you will share (using right click on folder and propperties), restart the service.  then connect to the folder from windows. folder should be available to same workgroup as windows uses.
 
In ubuntu configuring Samba is easy. In debian it's slightly more complicated.

---

### Post by mikodo on 2012-11-05
Thanks, mastablasta.

I'll do more reading about sharing with Samba, then.

---

### Post by wheeze on 2012-11-05
I've never had a problem reading or writing to NTFS partitions. No obvious CPU usage either. I have two disks in my computer, one for Linux and one for Windows. I regularly access the Windows disk from Linux.

---

### Post by mikodo on 2012-11-06
*Sorry, double post*

---

### Post by mikodo on 2012-11-06
@wheeze.

Thank you, for sharing your experience with read/write in NTFS.

It is good to know that you (and probably many others), are not seeing a problem with this.

You have given me more to contemplate and choose from.

The machines I am wanting to use, are of reasonable specs. This one is Intel integrated graphics  -quad core, 2.4 Ghz (nice of them to provide drivers for linux), with RAM 4-8 Gb, as an example, so they are not too old, or under powered. (I don't game).

---

### Post by mastablasta on 2012-11-06
what does this mean?
> home wired connection (not network)
 
are you using crossover cable? 
 
the easiest way is to have a router or at least a switch, connect the mashcines, share the folders on both mashcines (i think in windows you also need to share the drive to share the folder), then restart the samba service and see if the computers can see eachother. sometimes i had to reboot one or both mashcines to see them. 
 
also it helps that maschines are in same network workgroup.

---

### Post by mikodo on 2012-11-06
*deleted*

---

### Post by mikodo on 2012-11-06
> **mastablasta said:**
> what does this mean?

 
are you using crossover cable? 
 
the easiest way is to have a router or at least a switch, connect the mashcines, share the folders on both mashcines (i think in windows you also need to share the drive to share the folder), then restart the samba service and see if the computers can see eachother. sometimes i had to reboot one or both mashcines to see them. 
 
also it helps that maschines are in same network workgroup.I was thinking of using a crossover cable.

If I keep it simple and follow your advice, using samba through your easiest way, sounds feasible.

Thanks again!

---

