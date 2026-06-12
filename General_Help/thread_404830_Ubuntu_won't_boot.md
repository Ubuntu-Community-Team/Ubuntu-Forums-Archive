---
title: "Ubuntu won't boot"
date: 2007-04-08
forum: General Help
---

### Post by AlexanderPetros on 2007-04-08
I've somehow managed to stop my system from booting. I installed Ubuntu about two months ago and have run it without any problems. Today I put a second hard drive in the computer. I formatted it in Gnome Partition Editor and mounted it. I was able to see it all right. Then following [http://smorgasbord.net/how_to_install_second_hard_drive_ubuntu_linux](http://smorgasbord.net/how_to_install_second_hard_drive_ubuntu_linux) I added "/dev/hdb1 /mnt/drived ext3 defaults 0 0" to /etc/fstab and rebooted. The computer rebooted, went past the BIOS startup screen and then just hung with a blinking cursor. I tried booting with the 6.10 installation CD and was able to mount the main hard drive (everything's still there) and remove the line I added. This didn't help anything. I still just get a blinking cursor when I boot. No indication that it's reading anything from the hard drive. Any suggestions? I'm new to Linux, so I'm hesitant to mess with things too much without direction.

Thanks

---

### Post by AlexanderPetros on 2007-04-08
Okay, I was too quick to post here. The problem was the boot order. For some reason the BIOS wanted to boot from the new drive before the old drive. It's fixed. I withdraw my question.

---

### Post by WiseElben on 2007-04-08
If you removed the line, then your new HD should not be "visible." Try unplugging the new HD physically (just the power cord) and see if that does anything. I think what's happening is that you have set your new HD as the default, and being the default with no boot loader on it, it doesn't boot anything.

EDIT: Ah, I did not refresh before I posted. Good luck with Ubuntu.

---

### Post by LenzM on 2007-04-08
And instead of
```
/dev/hdb1 /mnt/drived ext3 defaults 0 0
```

you should replace the last 0 with a 2.

```
/dev/hdb1 /mnt/drived ext3 defaults 0 2
```

This tells it to check the drive for errors on boot, the only drives that should have 0's at the end are ones that you boot as read-only, like if you have a windows ntfs drive that you read but don't edit from linux.

---

