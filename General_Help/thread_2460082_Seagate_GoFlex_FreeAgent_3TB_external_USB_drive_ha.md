---
title: "Seagate GoFlex FreeAgent 3TB external USB drive has stopped being recognized"
date: 2021-04-02
forum: General Help
---

### Post by emonti on 2021-04-02
Hi,

I have been using a **Seagate GoFlex 3TB external USB drive** for about the last 10 years, mostly on **Ubuntu 16.04 LTS**.

Generally I had no problems although *very occasionally* it would seem to be asleep or hibernating and I had to unplug and replug it in/repower up the laptop to get it to work again. (I also read on other threads that these drives were - at least until a few years back - not linux-friendly, and there have been a few threads on the internet regarding the sleep mode, on linux.)

All that said, the other day, **the drive** **stopped being recognized** at all, on **ubuntu 16.04** or **20.04.2** (I tried booting from these two different live usb thumb drives). The only thing I can think may have had something to do with the problem is that shortly before it stopped working, I issued a umount -a command. Perhaps this was a too abrupt/non-graceful command.

**Lights on the drive itself:** when plugging in the power cable all the lights briefly flash on before going out completely. When I then plugin the usb cable into my laptop, there is a single light that comes on(after a short delay) and just seems to be quite dimly lit. 

**The drive no longer spins.** There is no humming anymore.

I have issued the following commands to try to locate any mention of the drive:

```
dmesg
tail -f /var/log/syslog
sudo parted -l
sudo lshw -C storage
lsusb -v
sudo fdisk -l
```

None of the above appear to indicate the drive is being recognized.... although some of the output may help to diagnose the problem, if someone can interpret the output.

I have tried booting into a windows partition, too, to see if it is recognized there, but I get the same result. Also, I tried plugging the drive into 2 different laptops and, again, the result is no different.

The drive was formatted **NTFS**, as part of the initial, factory setting.
 
If anyone can assist, that would be great.

---

### Post by ActionParsnip on 2021-04-02
If you run a chkdsk on it in Windows does it help?

---

### Post by emonti on 2021-04-05
ActionParsnip, I think chkdsk can only be run on a disk that is showing up/being detected by the OS.

I'm not even at that stage.

(I did see a message somewhere in the logs, which was not concrete enough but said something like 'bad cable?' It could be a bad cable but the cable has not been under any strain, and also the problem coincided with a umount, so I suspect it may have balked at the abruptly terminated connection.)

I am trying to avoid having to take the drive in because, if I can avoid the potential loss of data by resolving the problem myself, I would prefer that. Also, I sense technicians may see dollar signs, when someone brings a 'sick' hdd to them with a lot of data on it.

---

### Post by rbmorse on 2021-04-05
By all means try a different USB cable, and connect it to a different port on the computer if you can. Both are know to be genetically suicidal.  

With a ten year old drive, the problem could well be mechanical or electrical as the unit is about seven years beyond its engineered design life. That the drive no longer spins up would point in that direction, albeit not conclusively. 

Perhaps you have another wall-wart style power adapter with the same voltage and plug configuration you could try?

---

### Post by TheFu on 2021-04-05
There's nothing to be done when the drive refuses to spin up. Drive controller boards do fail.  Data recovery services usually charge about US$3K to replace them and provide a drive with the recovered data.  Backups are much cheaper.

10 yrs is a very long life for any spinning rust HDD. Count yourself lucky to get over 8 yrs.
Do you have backups?

A hail Mary play would be to put the drive into rice inside a ziplock bag and put it into the freezer for a few hours.  Then connect it up and pray it works for an hour or so as you pull the most critical data off. If it doesn't spin up, hit it lightly with a pencil. That might de-stick it. If it is spinning, DON'T HIT IT! That could crash the heads and definitely lots of data loss. Even $3K won't be able to recover.

I doubt any of this will work.  That data is gone, probably.

---

