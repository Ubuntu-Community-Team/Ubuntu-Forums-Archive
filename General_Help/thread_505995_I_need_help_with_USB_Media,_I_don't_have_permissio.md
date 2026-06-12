---
title: "I need help with USB Media, I don't have permission to my own USB drive :("
date: 2007-07-21
forum: General Help
---

### Post by Richmoar on 2007-07-21
So yeah, whenever I try to plug my USB drive(it's a "titan" brand 2 gig flash drive) on one USB slot it isn't recognized yet the other slot reads the drive. Now whenever I try to write files to it or take files from it(the flash drive) to my laptop it says I do not have the required permissions.

Granted the same thing happened(actually started) while using Fedora Core 6 which is a problem that has been haunting me ever since. ):<

 So If someone could help me access my sweet sweet files I'd appreciate it. ;)

---

### Post by nga911 on 2007-07-21
is it in ntfs format ?:)

can you copy from it !

---

### Post by Richmoar on 2007-07-21
Well I tried again a few minutes ago and I could get files from the flash drive to my laptop! :D

But I still cant write to it :(

Also how can I change the format of the flash drive?

---

### Post by splintercellguy on 2007-07-21
To write to NTFS you need NTFS-3G. Do sudo apt-get install ntfs-config and run the NTFS Config Utility in System->Admin I think.

---

### Post by nga911 on 2007-07-21
you can format it ( and lose the data on it ) to fat or fat32 .... or just do what "splintercellguy" sayed


Edit: But maybe it is easier to boot with ubuntu liveCD and go to qtparted (or was it gtparted?) and do it graphically.

---

### Post by Richmoar on 2007-07-21
I dont think you guys understand.

It's not a USB hard disk it's just a pen drive a little one. Do I really need to format? All I want is permission to write to it.

---

### Post by iDleR on 2007-07-21
No, but if it's an NTFS fs you have to do what splintercellguy just said

---

### Post by Richmoar on 2007-07-21
Ok then, thanks for all the help. =\^ _ ^/=

---

