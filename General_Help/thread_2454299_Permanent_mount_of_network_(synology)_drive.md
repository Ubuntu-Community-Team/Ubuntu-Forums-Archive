---
title: "Permanent mount of network (synology) drive"
date: 2020-11-26
forum: General Help
---

### Post by sross44 on 2020-11-26
Hi all. I'm new to Linux and Ubuntu. I'm making the switch for stability purposes from Windows for a Plex Server that I run in the home. Anyway... I have a Synology NAS that I've mounted to a folder inside Ubuntu. I did so based off the info from Synology at [How to access files on Synology NAS within the local network (NFS) | Synology Inc.]("https://www.synology.com/en-us/knowledgebase/DSM/tutorial/File_Sharing/How_to_access_files_on_Synology_NAS_within_the_local_network_NFS")

How do I set it up so after reboot I don't have to remount the drive again? Any information/help would be super appreciated. And to all the folks here in the US, Happy Thanksgiving!

---

### Post by CatKiller on 2020-11-26
You set which partitions get mounted where with /etc/fstab (the filesystem table configuration file).

I've got several lines in mine like ```
diskstation:/volume1/downloads  /mnt/nfs/downloads      nfs     auto,noatime,nfsvers=4       0       0
```

"diskstation" is in my /etc/hosts, so I can just have that there, otherwise I'd specify the IP address of my NAS.

---

### Post by sross44 on 2020-11-27
Thanks for this. I'm still completely confused though. Like I said I'm completely new to linux so trying to learn the ropes here. 

This is my current setup. I have a media folder on my synology NAS. 192.x.x.x:/volume1/Media I then mounted it to home/sross44/media

That's working perfectly... but every time I reboot I'm losing it. Is there a simple line that I use to make that mount perm? I tried what you had above with the right values and I'm lost. Sorry for being such a newbie!

---

### Post by CatKiller on 2020-11-28
That *is* the simple line that makes it permanent. It's just a text file that gets read at boot, and the things in it get mounted.

The syntax for the mount command and the entries in fstab are pretty much the same, but the fstab entries have to go in a particular order: what you want mounted, where you want it mounted, what type of filesystem it is, options that you want to use, and the two numbers that I can't remember what they're for (one of them is for whether you want it to be included in the periodic bootup filesystem check). 

Case is important (Media is not the same as media), the mount point (where you're mounting it to) needs to exist, and you need to specify the full path (/home is not the same as home). If you're using NFS to communicate with the NAS then that needs to be enabled on the NAS; if you're using something else then the entry in your fstab will be different. 

If you want to test your entry without rebooting you can use ```
sudo mount -a
``` which will mount everything in fstab, skipping anything that's already mounted. If you want to unmount something so you can try again, you can use ```
sudo umount <mount point>
``` (note that it's umount, not unmount) 

If you're still having trouble, post the full mount command that you're using and someone should be able to help you turn that into an fstab entry. The **man mount** and **man fstab** manpages *do* contain useful information, but they aren't as clearly written as some.

---

### Post by sross44 on 2020-11-28
So this is my mount code that I entered.... I copied it from the symbology website and altered it to my needs. Like I said I’m a complete newbie to Linux so maybe I didn’t mount it correctly but it does work for now, minus the reboot issue. How do I about taking this and making it in to the fstab entry like you mentioned so it’s a perm mount? 
[COLOR=#2E3742][FONT=&amp]
```
[/FONT][/COLOR][COLOR=#2E3742][FONT=Verdana]mount&#8195;-t&#8195;nfs 192.168.1.153:/volume1/Media[/FONT][/COLOR][COLOR=#2E3742][FONT=Verdana]&#8195;/home/sross44/Media[/FONT][/COLOR][COLOR=#2E3742][FONT=&amp]
```

[/FONT][/COLOR]

---

### Post by CatKiller on 2020-11-28
> **sross44 said:**
> So this is my mount code that I entered.... I copied it from the symbology website and altered it to my needs. Like I said I’m a complete newbie to Linux so maybe I didn’t mount it correctly but it does work for now, minus the reboot issue. How do I about taking this and making it in to the fstab entry like you mentioned so it’s a perm mount? 
[COLOR=#2E3742][FONT=&amp]
```
[/FONT][/COLOR][COLOR=#2E3742][FONT=Verdana]mount&#8195;-t&#8195;nfs 192.168.1.153:/volume1/Media[/FONT][/COLOR][COLOR=#2E3742][FONT=Verdana]&#8195;/home/sross44/Media[/FONT][/COLOR][COLOR=#2E3742][FONT=&amp]
```

[/FONT][/COLOR]

I think the fstab equivalent of what you've put there should be ```
192.168.1.153:/volume1/Media  /home/sross44/Media      nfs     auto       0       0
```

You can use **mount -a** to test it - you should get an error message if there are any problems. 

I can't remember why I put the NFS version in mine - it was a long time ago, on a previous computer, that I set mine up. Maybe it's still needed, maybe it's not. Maybe it depends on what settings you've got on the NAS. 

You'll also need to be sure on the case: both the Synology NAS and your Ubuntu machine are case-sensitive by default, and the M in Media has been sometimes lower case and sometimes upper case with what you've written, so it's a thing to check.

As a more-or-less orthogonal matter, mounting things to within a Home directory gives me the willies. Mounting to somewhere else and then having symlinks from the Home directory to the mount point seems much nicer to me. It's your system, though, so you should mount to wherever makes most sense to you.

---

### Post by sross44 on 2020-11-29
I got it to work! Thank you for your help!! Most appreciated.

---

