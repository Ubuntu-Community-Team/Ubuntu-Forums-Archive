---
title: "cant login after cloning disk"
date: 2024-06-29
forum: General Help
---

### Post by pagusi on 2024-06-29
Greetings,
i've cloned a Kubuntu Drive. Now i can only log into Kubuntu(on the new drive) if i use the virtual keyboard for the underscore in my Password. 
After the first login this problem disappears. So if i lock my laptop and login again i can do that normally. If I reboot only with the virtual keyboard.
Any ideas?
-Paul

---

### Post by TheFu on 2024-06-29
Did you remove the original drive?  UUIDs cannot be identical on two disks/partitions/file systems.
Were the source and target drives using the same sized blocks?  512b and 4K are the normal choices.

Was one SATA and the other NVMe?  Those will have different device names, so if the mounts use device names, not LABELs or UUIDs, then those won't work until you manually fix it everywhere necessary.  At a minimum, that would be in the /etc/fstab

Are there other storage devices connected - beyond just the new drive? If so, what is on them?

---

### Post by pagusi on 2024-06-29
The original drive is not connected anymore, one was mSata and the new one is M.2 but still SATA. And IF that was the problem wouldnt this be a consistent problem? I mean because on the second login it works.
And there are no other storage devices connected

---

### Post by oldfred on 2024-06-29
Booting with grub relies on the UEFI settings for USB ports. Or you have to have USB enabled or full USB support or whatever your system requires.
An UEFI firmware update could have reset UEFI to defaults & you need to reset it.

Since able to boot, this may not show anything, but report does show details of your installs. 
lease copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

This is why I prefer new installs to new drive & restore from your backup. Then you also verify that your backup is complete while still having old drive to get anything you may have missed.

---

### Post by pagusi on 2024-06-29
[https://paste.ubuntu.com/p/KQhCH95y72/](https://paste.ubuntu.com/p/KQhCH95y72/)

what would have been important to mention is that i switched not only from one ssd to another but from one laptop to another. 
Another thing that i could think of why that problem appears, is that the old laptop had the ANSI US layout and the new one has the german DE ISO layout. My first guess was that the layout wouldnt be correct at startup.

---

### Post by pagusi on 2024-06-29
I've solved it. The keyboard layout didnt change before first login. 

Problem solved through:
sudo dpkg-reconfigure keyboard-configuration
sudo service keyboard-setup restart

---

### Post by TheFu on 2024-06-30
> **pagusi said:**
> [https://paste.ubuntu.com/p/KQhCH95y72/](https://paste.ubuntu.com/p/KQhCH95y72/)

what would have been important to mention is that i switched not only from one ssd to another but from one laptop to another. 
Another thing that i could think of why that problem appears, is that the old laptop had the ANSI US layout and the new one has the german DE ISO layout. My first guess was that the layout wouldnt be correct at startup.

If a different keyboard is found, then the keymapping will be different.  There's your answer.  Reset the password.

---

