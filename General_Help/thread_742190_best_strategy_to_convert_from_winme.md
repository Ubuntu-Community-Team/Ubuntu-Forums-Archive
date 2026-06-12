---
title: "best strategy to convert from winme"
date: 2008-04-01
forum: General Help
---

### Post by augrrr on 2008-04-01
I have a 1ghz, 768meg ram, 120gig hdd winme system which I am looking to convert to ubuntu.  The live-cd (v7.04) seems to behave very nicely (although I wasn't able to figure out how to get dialup-internet working).  What's the best strategy to do the change-over?  I would like to retain access to all my existing data (approx 60meg).  I am not sure what ubuntu's "migrate" is designed to do.  Do I have to retain a shared FAT32 partition if I want to access my current old data and files?  I just want to access the data long enough to sort out what I want to keep. Should I establish separate partitions for /, /etc, /home, and so on?  I also have a spare 250meg external usb drive which I can currently access via a networked XP pc; the initial idea was to copy all the current winme data to that, and then access that drive later via direct usb connection or the network.  But will either approach be a problem if the current external drive is NTFS?   I am seeking our opinions on the best way to go about all this.

Thanks!
..augrrr

---

### Post by tangibleorange on 2008-04-01
hmm. I think in 7.04 there is an issue reading and writing to an NTFS drive, but in 7.10 it works without a hitch. I'd recommend the most recent version.

As for separate partitions, you only NEED '/' and a swap partition, but a lot of people like to create a seperate /home partition as well, to store their personal data. It's quite a good idea in general in case your root partition fails or something like that, or you simply want to upgrade without losing your files.

If you're using 7.04, I think the temporary shared FAT32 partition is a better idea.
If you're using 7.10, the external NTFS is probably better. You say it's networked though - networks can often be quite troublesome first time round. can you access the network/shared drive on the live CD?

---

### Post by augrrr on 2008-04-02
Yes...  I can access the networked drive with the LiveCD.  Meanwhile, I found a copy of 7.10 iso that I had downloaded a little while ago.  I created  a livecd of that.  That version  seemed to perform quite well too.  Thanks for your suggestions.  I think I'll do the external/networked drive approach to backup(copy) my entire winme file structure, and install Ubuntu with 100% ext3 format. I'm completely green installing Ubuntu so setting up a shared fat32 partition sounds confusing. I hope to just pick and choose the old files I want from the networked usb drive, or just plug it in directly.

---

### Post by tangibleorange on 2008-04-03
> **augrrr said:**
> Yes...  I can access the networked drive with the LiveCD.  Meanwhile, I found a copy of 7.10 iso that I had downloaded a little while ago.  I created  a livecd of that.  That version  seemed to perform quite well too.  Thanks for your suggestions.  I think I'll do the external/networked drive approach to backup(copy) my entire winme file structure, and install Ubuntu with 100% ext3 format. I'm completely green installing Ubuntu so setting up a shared fat32 partition sounds confusing. I hope to just pick and choose the old files I want from the networked usb drive, or just plug it in directly.

that certainly sounds like the best way to do it to me. I hope you like Ubuntu!

---

### Post by sekinto on 2008-04-03
Actually you don't even need a swap partition, you can make a swap file. It is just a better idea to have a swap partition, just like it is a good idea to have a separate /home partition (and some people like to have a separate /boot partition to).

---

