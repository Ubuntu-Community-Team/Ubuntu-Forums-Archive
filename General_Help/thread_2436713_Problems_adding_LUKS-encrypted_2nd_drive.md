---
title: "Problems adding LUKS-encrypted 2nd drive"
date: 2020-02-11
forum: General Help
---

### Post by ofnuts on 2020-02-11
I'm trying to add a second disk (HDD, first drive is SSD) on a  freshly  installed Kubuntu 19.10 (where the boot disk is already LUKS   encrypted).  
I open the KDE Partition Manager and 


[LIST]
[*]select the sda drive (the HDD),
[*]add a GPT partition table,
[*]add a primary partition with
[LIST]
[*]ext4 file system
[*]LUKS encryption option checked
[/LIST]

 
[/LIST]
 At some point I'm asked for a passphrase and a mount point, so everything looks fine. I "apply" this, and ask the PM to rescan and the ext4-under-LUKS partition is there. 

I reboot. I am of course asked the SDD passphrase, but not the HDD passphrase (which didn't bother me   too much, I was hoping that the partition manager would also create a   keyfile to be able to mount the disk without intervention).


[LIST]
[*]the 2nd disk is not mounted
[*]there is an an entry for it in /etc/fstab
[*]there is no entry for it in /etc/crypttab
[*]reboot  takes a lot longer, from approx. 40" (when the HDD was blank) to 2'10. systemd-analyze says that  system boot tile is normal (17") but user-space is slow (1'55").
[*]the "Encrypted drive" appears in Dolphin "places".
[*]if I click on it I get asked the passphrase
[*]then I get an error bar in Dolphin saying that the device /dev/dm-3 is already mounted
[/LIST]

Is all this normal? In my previous machine (16.04) I had a similar setup but I did it by   hand, so I can hopefully redo it, but I'm just hoping that 19.10 can do   it in a more automated way, so what is missing? Did I miss an option in   the Partition Manager? Or is the LUKS support incomplete? Is the increased user-space boot time normal? How can I analyze it?

Possibly related, I sometimes get messages about the inability to create file-io slaves (from memory).

---

### Post by EuclideanCoffee on 2020-02-12
I'm not familiar enough with KDE to give advice. I was able to accomplish this with gnome-disk because it has an auto-mount feature that helps with the crypttab and fstab feature. If KDE isn't your only option, I would recommend using gnome-disk, but the choice is yours. Good luck!

---

### Post by ofnuts on 2020-02-12
Can you describe your setup (/etc/crypttab, /etc/fstab, keyfile location)? Because [I have read that you cannot get an auto-mount on Ubuntu,]("https://askubuntu.com/a/541352/548230") since all disks are decrypted before any is mounted, so you cannot put the keyfile for your 2nd disk on an encrypted partition. But things could have changed in recent versions?

---

### Post by EuclideanCoffee on 2020-02-12
I'd be happy to, but I removed this configuration and don't intend to have an encrypted disk. Sorry. :(

I do know that I had this as a working configuration.

From what I recall doing, the formatting, auto-mounting, and encryption features are all available on 18.04 LTS gnome-disk.

---

