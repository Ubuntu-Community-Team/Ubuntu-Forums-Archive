---
title: "cant boot off of clone."
date: 2016-01-15
forum: General Help
---

### Post by mikee2 on 2016-01-15
[COLOR=#111111][FONT=Ubuntu]I recently made a clone of two partitions of my 64bit Ubutnu 14.04 install, but can not boot off the new clone.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]First off let me say , the source disk was larger than the destination, so I decided to only copy the partitions (and not the entire disk using) the dd method. Before doing though, this I prepared the destination disk by creating a replica of the source partition table on the destination disk as described by Malte Skoruppa [here]("https://askubuntu.com/questions/409204/how-to-clone-to-a-smaller-harddisk").
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The method of cloning was to plug in an external drive that had working clone of my original install and copy that using:[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
```

[FONT=arial]sudo -s 
dd if=/dev/sda1 of=/dev/sdb1 & pid=$! 
while kill -USR1 $pid; do sleep 1; done[/FONT]
```
[/FONT][/COLOR]
```
[FONT=arial][COLOR=#111111]dd if=/dev/sda2 of=/dev/sdb2 & pid=$! 
while kill -USR1 $pid; do sleep 1; done[/COLOR][/FONT]
```

[COLOR=#111111][FONT=Ubuntu]While I thought this was going to work, I had my suspicions that the boot part might not be configured, so I booted up in [/FONT][BOOT-Repair LIVE]("https://help.ubuntu.com/community/Boot-Repair")[FONT=Ubuntu] to see if I could fix the issue. I selected to reinstall GRUB and purge the old one, but I still can not boot from this drive.[/FONT]
[/COLOR]
[COLOR=#111111][FONT=Ubuntu]In any case, I copied the output to file to have a look below: [/FONT]
[FONT=Ubuntu](be advised that /dev/sda/ is the destination drive of the cone that isnt working and that /dev/sdb was the source during the dd cloning operation.

[/FONT][/COLOR][http://pastebin.ubuntu.com/14504085/](http://pastebin.ubuntu.com/14504085/)[COLOR=#111111]
[/COLOR]
[COLOR=#111111][FONT=Ubuntu]If someone could have a look a this output, and my method, and tell me where I went wrong, or what needs to be fixed I would be happy[/FONT][/COLOR]

---

### Post by Bucky Ball on 2016-01-15
That's a bit of a mess. You've ended up with two UEFI partitions and no grub installed anywhere.

Could you run boot repair again, please, and choose 'Advanced' and select to install grub to sda. Not a partition, just sda. Once that's done, finish up and reboot.

That may get somewhere, but you need more expertise than I have to help clean up. Those two EFI partitions I would imagine will cause issues. I'm no expert with EFI but there's others about who are and will hopefully be able to lend a hand.

* You made a clone on the internal disk of the working clone on an external disk. How did you know it was a working clone? Were you able to boot that from the external drive, or from another clone of it, and all ran normally?

---

### Post by leunam12 on 2016-01-15
Clonezilla is your friend.

---

### Post by mikee2 on 2016-01-15
Thank you Bucky Ball for your reply! Of course its a mess, I have no idea what im doing and the documentation I found online was hardly adequate to help a novice like me.  :D  (Also I tried 5 times using clonezilla and I couldnt figure it out that way. It has issues with smaller disks being the destination)

> **Bucky Ball said:**
>  You made a clone on the internal disk of the working clone on an external disk. How did you know it was a working clone? Were you able to boot that from the external drive, or from another clone of it, and all ran normally?

Heres how it went: I have a nice stable working environment that has all the app I like on an internal 128GB SSD so I cloned that to a 250BG external drive. Once I realized that the drive i made the was older and harder to hookup (its a SATA that needs a converter etc) I decided it would be best to try and jsut clone it to a 64GB flash USBd rive. I know the clone on the 250GB drive works because I can actually boot to it. 

The reason there might be no grub is because I asked BOOTpart LIVE to reinstall it, but it looks like it failed. 

EDIT: I successfully reinstalled GRUB and got to booting off of the 64G clone (great news) but it is VERY VERY slow to load. The last part of the GRUB repair/install with BOOTrepair said something about [B]make sure your BIOS on sda/EFI/ubuntu/shimx64.efi file ! 

[/B]How do i go about this?When i boot ubuntu there are several options:

[IMG]http://s14.postimg.org/uq67iq52p/bootmenu.jpg[/IMG]

If i choose the EFI menus I get into some text mode UI where they ask about a key for the boot, but I dont know what or where to choose the file. 
ALmost done !

---

### Post by Bucky Ball on 2016-01-15
Yes, Clonezilla will only clone a partition to a target partition that is the same size or larger (which makes sense). There is other software I think that doesn't have this limitation (perhaps fsarchiver is one of them). 

You have marked this thread as solved. If this is the case, protocol here is to share with the community your fix to help others, so please do. :)

---

### Post by mikee2 on 2016-01-16
ok thank you, I still need to figure the rest out, but I guess thats a new thread. How do I share this then?

---

### Post by Bucky Ball on 2016-01-16
Sorry. My mistake. You re-installed grub. Yes, UEFI questions about this probably better on a new thread as you can now boot cloned OS. Good luck.

---

