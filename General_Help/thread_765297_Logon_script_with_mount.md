---
title: "Logon script with mount"
date: 2008-04-24
forum: General Help
---

### Post by psmul on 2008-04-24
Hi,

I have a freshly installed Hardy Heron and it seems it doesn't auto mount my windows hd's.
How can i auto mount a disk when i log on as my user (and not when just anyone logs in)? Where do i put my script that doesnt need the 'sudo' command. Or is there an easier way to do this?

---

### Post by psmul on 2008-04-26
bounce

---

### Post by fragos on 2008-04-26
Hardy has changed the automatic mounting of other dives and or partitions. It automounts those associated with this installation but still shows the unmounted ones in the naultius places panel. In that panel I click an unmounted drive and it mounts. The second click shows the files. I have multiple partitions but defiantly, none are Windows but I'd think it would still work the same way. The normal way to automount is to edit /etc/fstab.

---

### Post by psmul on 2008-04-27
ok thanks, ill that a go

---

### Post by psmul on 2008-05-03
sorry for the late reply, but if it still matters it did the trick.

/dev/sdb1	/media/win_data	ntfs	defaults	0	0

added the above to /etc/fstab and it now mounts it on boot.

Thanks

---

