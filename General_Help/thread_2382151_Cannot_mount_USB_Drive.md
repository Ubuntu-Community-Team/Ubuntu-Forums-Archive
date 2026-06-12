---
title: "Cannot mount USB Drive"
date: 2018-01-09
forum: General Help
---

### Post by tjuklondon on 2018-01-09
I am running Ubuntu 16.04 on VM Virtual box on a windows 10 machine. I am having trouble mounting all sorts of USB drives. 

I can see the drive in gnome-disks, but when I try to edit the mount options to mount at start uo I get the following message:

Error adding new /etc/fstab entry
An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender=":1.131" (uid=0 pid=6948 comm="gnome-disks ") interface="org.freedesktop.UDisks2.Block" member="AddConfigurationItem" error name="(unset)" requested_reply="0" destination=":1.55" (uid=0 pid=1502 comm="/snap/udisks2/100/libexec/udisks2/udisksd ") (g-dbus-error-quark, 9)

I should add that I don't mount the drive in Windows, and tick it on the USB settings in VB.

I am used to drives just appearing in the folder structure, and whatever drive I insert I still have this problem.

Any help appreciated. Thanks!

---

### Post by tjuklondon on 2018-01-14
Hi I just opened gnome-disks via terminal and the following message appeared:

Error calling Drive.Ata.PmGetState: GDBus.Error:org.freedesktop.DBus.Error.AccessDenied: An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender=":1.119" (uid=0 pid=4876 comm="gnome-disks ") interface="org.freedesktop.UDisks2.Drive.Ata" member="PmGetState" error name="(unset)" requested_reply="0" destination=":1.51" (uid=0 pid=1589 comm="/snap/udisks2/100/libexec/udisks2/udisksd ") (g-dbus-error-quark, 9)

Maybe that gives a bit more info to someone?

Help appreciated, many thanks!

---

