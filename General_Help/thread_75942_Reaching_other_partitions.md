---
title: "Reaching other partitions"
date: 2005-10-14
forum: General Help
---

### Post by nrichar2 on 2005-10-14
i am a first time linux user taking the plunge with Ububntu. I dont know much, so i installed Ubuntu onto my windows xp machine. before i hade three partitions over two drives, windows, a space for music, and one for movies, all ntfs. now i have my linux partition too. what i need to know is how/if i can access my music partition from Ubuntu. like i said, im completely new, im not a big time computer user, but i we use linux in my programming class and i like it much better than windows so i thought i better give it a try at home. 

thanks,
Nic

---

### Post by jackmacokc on 2005-10-14
[QUOTE=nrichar2]i am a first time linux user taking the plunge with Ububntu. I dont know much, so i installed Ubuntu onto my windows xp machine. before i hade three partitions over two drives, windows, a space for music, and one for movies, all ntfs. now i have my linux partition too. what i need to know is how/if i can access my music partition from Ubuntu. like i said, im completely new, im not a big time computer user, but i we use linux in my programming class and i like it much better than windows so i thought i better give it a try at home. 

thanks,
Nic[/QUOTE]

easy... [try this]("http://ubuntuguide.org/#windows") and let us know if you need any more help.

---

### Post by panocrat on 2005-12-03
hey jackmacokc, i'm having a similar problem and hope you might be able to help. i tried the advice from the link you supplied, but i get an error telling me the device doesn't exist. i think i know why, it's because i have a SATA hard drive which is seen by Ubuntu as a SCSI device. as such i've attempted to edit the sudo mount /dev/hda1 command to reflect how Ubuntu sees my disk, but to no avail. looking at device manager i can see the details of the SATA drive, but i'm not sure which key/value i should be looking at. i've tried a few...any help appreciated!

---

### Post by Bachstelze on 2005-12-03
have you tried fdisk -l to locate your windows partitions ?

---

### Post by panocrat on 2005-12-03
HymnToLife, thanks, very useful advice...i can now see the NTFS partition (was called sda1 rather than hda1...which information was actually visible in disk manager).

---

