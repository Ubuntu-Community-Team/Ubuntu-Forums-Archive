---
title: "New Partition?"
date: 2007-05-14
forum: General Help
---

### Post by lonjim2 on 2007-05-14
Greetings fellow Ubuntu users!

So a bit of a challenge...I'm getting ready to convert this one desktop I have to upgrade to Feisty, but I want to do a clean install.  I have 30 Gb of local documents and other files I want to archive.  I have two external hard drives, but both seem to stop copying files after only 3 minutes (both firewire and USB!).

I tried to overcome this by creating a new partition in GParted that I can dump the files onto and then access them from the new Feisty install afterwards.  Only problem is I can't figure out how to mount this new partition HDC3.  I try: > sudo mount -t ext3 /dev/hdc3 /media/hdc3 but have no success.  It says the mount point does not exist.

I'm just really not good with the terminal so any help is most appreciated.

Thanks all.

---

### Post by taurus on 2007-05-14
You need to create /media/hdc3 first before you can mount /dev/hdc3 to it.

```
sudo mkdir /media/hdc3
sudo mount -t ext3 /dev/hdc3 /media/hdc3
df -h
```

---

### Post by lonjim2 on 2007-05-14
Ahhh! This is perfect, thanks for the lesson of the day!

---

