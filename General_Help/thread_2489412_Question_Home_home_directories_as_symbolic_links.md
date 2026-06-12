---
title: "Question: Home home directories as symbolic links"
date: 2023-07-29
forum: General Help
---

### Post by Old Jimma on 2023-07-29
Hello Ubuntu Forum:

I have a rasberry pi that has a 128Gb microSD chard that is supposed to be where my home directory is stored. **The pi uses the Ubuntu 22.04 opprerating system.**

Also, I have a 1Tb SSD that contains a backed-up copy of another computer's home director that was created using rdiff-backup. That SSD has much more data on it than 128Gb.

I want to use that 1Tb SSd as my pi's home directory.... using this plan:


1. create links (using Nautilus) of the Desktop, Documents, Downloads, Music, Pictures, Video folders that are on the 1Tb SSD drive

2. delete folders with the same names in the home directory on the microSD card,

3, move the symbolic links created in step 1 to the home directory on the microSD card.

**Will this work? Or, is there something safer and better?**

**Also, I will mount another 1Tb SSD drive to the pi and use rdiff_backup to backup the home directory on the pi's microSD card.**

Will this work?

Thank you!
Old Jimma

---

### Post by TheFu on 2023-07-29
It would be cleaner to mount the SSD to /home directly.  I do something like this:
```
$ df -Th     # I removed other mounted file systems for clarity
Filesystem                        Type      Size  Used Avail Use% Mounted on
/dev/mapper/vg01-home01           ext4      9.8G  5.4G  3.9G  58% /home

```

There are 500 other options.  Many people would move the larger document/music/video directories to another disk and use symlinks for those directories in their HOME to that other storage.   Something like this:
/home/thefu/Documents ---->   /media/data/Documents
That is created by running these commands:
```
cd ~thefu
ln -s /media/data/Documents
```
Simple.

---

### Post by Tadaen_Sylvermane on 2023-07-30
Just something to consider. I do this with several directories that don't change much between distros. Stuff like my flatpak data. So far /home/"$USER"/.var has caused some issue with some flatpaks not being able to work. I use bind mounts now. But just something to keep in mind. While symlinks will work for the most part there will occasionally be something that won't work right. I don't think there is a definitive list on this though. Trial and error type of thing.

---

### Post by Old Jimma on 2023-07-31
Thank you again, The Fu.

I really am grateful for your help and advice.

I tried creating solf links to the home directory from the SD drive and it works well.

There were comments on other linux advice forums that doing this could result in not being able to reboot.

**This report does not confirm those warnings. Rather, this report confirms that The Fu's simple advice of creating softlinks for folders in the /home directory is easy... and works well.**


Thanks,
Old

---

