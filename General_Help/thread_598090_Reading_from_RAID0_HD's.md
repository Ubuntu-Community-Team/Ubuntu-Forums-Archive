---
title: "Reading from RAID0 HD's"
date: 2007-10-31
forum: General Help
---

### Post by Nexusx6 on 2007-10-31
Hey all, minor problem here and in need of a guide.

I have 3 hard drives in my computer, one of them is a 120gb  SATA that has Ubuntu installed, the other two are a fakeRAID0 that has Windows XP on it. Ubuntu "sees" the RIAD array, but when I double click so that I can read from it I get an error that involves "activating" the array through dmraid and mounting under a different device - things I'm really not familiar with :(

I've searched the forums and read the guide at [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto) but that guide focuses on installing Ubuntu to a fakeRAID, all I want to do is simply read from one. I would greatly appreciate help on this.

> fox@aurora-project:~$ sudo dmraid -ay
RAID set "nvidia_fidfcidf" already active
RAID set "nvidia_fidfcidf1" already active
fox@aurora-project:~$ sudo dmraid -r
/dev/sda: nvidia, "nvidia_fidfcidf", stripe, ok, 488397166 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_fidfcidf", stripe, ok, 488397166 sectors, data@ 0


---

### Post by Selfish Meme on 2007-10-31
I am guessing you are using NTFS as the filesystem in windows, if so you would need to mount the drive using ntfs-3g

sudo mount -t ntfs-3g  /dev/mapper/nvidia_fidfcidf1 /media/whereveryouwanttomount

*make the /media/whereveryouwanttomount directory first using sudo mkdir /medi.....

---

### Post by Nexusx6 on 2007-10-31
It worked, awesome! Thanks a ton, really :KS

---

