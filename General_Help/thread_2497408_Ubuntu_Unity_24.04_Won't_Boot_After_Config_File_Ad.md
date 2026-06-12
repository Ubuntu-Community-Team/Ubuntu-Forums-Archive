---
title: "Ubuntu Unity 24.04 Won't Boot After Config File Added"
date: 2024-05-03
forum: General Help
---

### Post by wmichaelb2 on 2024-05-03
I installed Unity 24.04 on a Latitude 6420 a few days ago, and have been working at building up the rest of the system. I've had a bit of trouble getting the trackpad to work smoothly, so I install the synaptics driver, and went through the options with the synclient command. But synclient doesn't save the settings after a reboot. I read to create a new synaptics.conf file in /etc/X11/x11conf.d, so I copied the one from /user/share/x11/xorg.conf.d to that location with a new name, and now the system won't boot. 

So I think no problem, I booted the USB drive that I installed the system from, opened a terminal, ran df, and it did not show the main SSD in the laptop as having been mounted. I ran fdisk -l, and found it labeled as sda1. Therefore, I ran:

sudo su
mount /dev/sda1 /mnt

And got an error message that says that /dev/sda1 is not a directory. Can someone please tell me what I'm missing here? I'd like to simply delete that directory, rather than reinstall. Thanks in advance.

---

### Post by currentshaft on 2024-05-08
b

---

