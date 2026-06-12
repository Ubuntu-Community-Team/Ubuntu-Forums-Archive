---
title: "Making Bootable Ubuntu penDrive from Live Ubuntu session"
date: 2015-04-21
forum: General Help
---

### Post by Harsh_Parikh on 2015-04-21
Hey Guys,
I am using Ubuntu Live session for my work as my Hard Drive is not working...
My friend wants the ubuntu in his pendrive....
But as I don't have original iso disk image(as It is in Hard Drive and it's not working)...
Can I do anything from the Live Session PenDrive..???
I am used to do it with dd command,

```
sudo dd if=/dev/sda1 of=/dev/sdc1
```

Here,sda1 is the live session pendrive partition and sdc1 is the other pendrive in which I want to make it bootable in Ubuntu...

Please HELP....

---

### Post by haplorrhine on 2015-04-21
[https://ubuntuforums.org/showthread.php?t=1874937](https://ubuntuforums.org/showthread.php?t=1874937)

See under Backup Utilities and Alternatives
[https://help.ubuntu.com/community/BackupYourSystem#Backup_Utilities](https://help.ubuntu.com/community/BackupYourSystem#Backup_Utilities)

I believe clonezilla is the standard bootable-backup creator, but I've never used it.

---

### Post by monkeybrain20122 on 2015-04-21
So there is no startup disk creator in the live session?  I think you have to download another iso from your life session to create the second live usb within the live session just as you would create a live usb in a normal ubuntu session, not by dd-ing your own live usb while it is running like this, moreover dd is kind of dangerous not sure why you want to do it that way. If you don't want to download another iso you can make a full install of Ubuntu into the 2nd flash drive from your live session in the same way you would install Ubuntu to your internal hard drive (provided the second flash drive is >= 8 G)

---

### Post by Harsh_Parikh on 2015-04-22
Thank you very much....Both Of you

---

