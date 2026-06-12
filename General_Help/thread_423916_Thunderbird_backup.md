---
title: "Thunderbird backup"
date: 2007-04-26
forum: General Help
---

### Post by ruialexbarbosa on 2007-04-26
Hi,

I want to upgrade from dapper to Feisty, but would like to keep my thunderbird settings. Where are they? (emails, accounts, contacts...)

Thanks

---

### Post by aysiu on 2007-04-26
If you're using Ubuntu's Thunderbird (installed through Synaptic, Adept, or Add/Remove), it's in /home/*username*/.mozilla-thunderbird (also known as ~/.mozilla-thundebird)

If your'e using Mozilla's Thunderbird (from the Mozilla website), it's in ~/.thunderbird

It's a hidden folder. You can view it by pressing Control-H (or, if you're using Kubuntu, pressing Alt-V, then H).

---

### Post by ruialexbarbosa on 2007-04-26
Thanks Aysiu,

and is it possible to change that path? Mine is in home, could I change it to another (fat32) partition? Better even, can I move my home directory to my fat32 partition?

Thanks

---

### Post by aysiu on 2007-04-26
> **ruialexbarbosa said:**
> Thanks Aysiu,

and is it possible to change that path? Mine is in home, could I change it to another (fat32) partition? Better even, can I move my home directory to my fat32 partition?

Thanks
I'm not sure if you can make a symbolic link from a FAT32 partition to Ext3. If you can, this is how you'd do it.

Let's say your FAT32 partition is mounted at /media/hdb1 (you can substitute in the actual mount point, whatever it is).

Type this command in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
ln -s /media/hdb1/.mozilla-thunderbrd ~/.mozilla-thunderbird
```

**Edit**: Never mind. Try this:
[Howto Thunderbird/Firefox profile share XP & Dapper](http://ubuntuforums.org/showthread.php?t=203524)

---

### Post by ruialexbarbosa on 2007-05-07
Hi,

I did it, but looks like nothing happened...

---

