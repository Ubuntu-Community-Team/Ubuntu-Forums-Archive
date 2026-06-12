---
title: "Reducing the damaged caused by a hard shutdown"
date: 2013-01-03
forum: General Help
---

### Post by Stonecold1995 on 2013-01-03
My brother has an HP laptop, but the battery is broken so unplugging it from a power source immediately shuts it down.  This happens fairly often and each time it risks data corruption.  So what's the best way to reduce the risk of data corruption when this *does* happen?  He uses the ext4 filesystem and has separate partitions for /home and / (even though they're on the same disk), but as far as I know that's the only safeguards he has against data corruption (and most people use that anyways).  What other things can he do to minimize the damage of a hard shut down?  Like, is there a way to increase the the write cache so data is synced to the disk at longer intervals (would that even help)?  He's using Kubuntu 12.10 on an HP Pavilion, btw.

---

### Post by Bucky Ball on 2013-01-03
Firstly, why is the power being cut??? Secondly, why not just shut down the machine, then cut the power? 

Bit confused with this one.

---

### Post by Stonecold1995 on 2013-01-03
> **Bucky Ball said:**
> Firstly, why is the power being cut??? Secondly, why not just shut down the machine, then cut the power? 

Bit confused with this one.

The power is sometimes accidentally cut because the power cord unplugs unexpectedly, and the damaged battery doesn't hold enough charge to keep the computer on nearly long enough to properly shutdown.  Until the battery problem is resolved, there will likely be more incidents where the power is suddenly lost, and I want to be able to minimize the chances of corruption too severe for the file system's journal or fsck to recover in the meantime.

---

### Post by Bucky Ball on 2013-01-03
Nasty situation. Replace the power cord or plug. There is not much you can do to prevent damage to the hard drive using software in that situation. If the hard drive is spinning when the power's cut it is in danger.

Back up everything.

---

### Post by cwsnyder on 2013-01-03
Nearly anything which would be better (zfs, btrfs) would require a complete re-installation, which would require a stable power source for the duration of the installation.

IMO, you should leave well enough alone and not use the laptop as a laptop, but only on as a desktop on a fixed desk until you get the battery replaced.

---

### Post by conradin on 2013-01-03
I agree with everyone else, replace the battery, and remove the physics of failiure. Just musing, I though, if you got a solid state drive you wouldnt get the plater / r/w head colisions, which would reduce damage to the device. Though you would still have other problems.

---

### Post by iponeverything on 2013-01-03
or you could keep rolling the dice -- over the years I have done hundreds of dirty shut downs and. Many because of bad laptop batteries that I didn't want to waste money on replacing. 

The only time really got burned was using ReiserFS. A dirty shut down on that system once resulted in a situation where I had a total loss..

In every other case, and their have been many - fsck - always fixed things up..

---

### Post by Stonecold1995 on 2013-01-03
Are there any software methods, like having the hard drive spin up only once ever 5 or 10 minutes to sync and then spin down?

---

### Post by tgalati4 on 2013-01-03
Not really.  It's hard to defend against that type of shutdown.  You could run off of a USB stick with provisions for storing data on the stick.  Read up on unetbootin.  But then you are running "Live" in RAM only and saving user data onto the USB stick.  When you lose power, at least your data is on the USB stick.

Sometimes a weak battery takes more power than usual, making the computer unstable.  Try running with a power cord without the battery.  And as others have suggested, used it as a desktop machine--don't move it around.  Otherwise you will be right back here on the forum asking how to recover data from a corrupted hard drive.

---

### Post by audiomick on 2013-01-03
> **Stonecold1995 said:**
> Are there any software methods, like having the hard drive spin up only once ever 5 or 10 minutes to sync and then spin down?

I haven't read all of every post here, but I assume that the "shutdown on dead battery" option in the power management is turned on. If the battery is not holding enough power even for that, I don't think you have a chance of any other method working that relies on the computer having power.

If you can't get a new battery or a new power supply that doesn't unplug itself, at least stick the plug in with duct tape or something until you can find a better solution.

---

### Post by BertN45 on 2013-01-03
Here I have the same type of problems, the electricity is lost a couple of times a day and for that I stopped using ext4. I lost between 20-50 songs that I had on my system, because of a zero file length. Currently I only use ext3 for my home partition. I think I remember that the difference is that ext4 keeps files cached even after the file is closed, while ext3 is writing the file to disk, if it is closed. You can force ext4 to behave more or less in the same way by adding data=journal to the mount option in fstab.

I did it at that time for the only partition of the system and I did:
Change journalling system/files
[COLOR="Blue"]sudo tune2fs -ojournal_data /dev/sda1[/COLOR]

Fstab entry in /etc/fstab
# / was on /dev/sda1 during installation
UUID=af8c719f-9a9c-473f-881e-d9aad93d6765 /               ext4    [COLOR="blue"]data=journal[/COLOR],errors=remount-ro 0  1

You will have to adapt it for your situation. You can google "data=journal" and you will find more detailed information and backgrounds.

Nowadays usb drives are relatively cheap and I also use the deja-dup backup program and make back-ups each week automatically. In the past I used (g)rsync, but that will overwrite the old correct files with the new and corrupted file automatically. Deja-dup will allow me to get back files from older dates, if needed. For my brother in law I do the same using a network drive on another computer.

---

### Post by Stonecold1995 on 2013-01-03
If the hard drive is unmounted will it spin down?

---

### Post by cwsnyder on 2013-01-06
> **Stonecold1995 said:**
> If the hard drive is unmounted will it spin down?That depends on your power management settings.

---

### Post by Bucky Ball on 2013-01-06
Please, just fix the power cord and be done with it ...

***Thread Closed***

---

