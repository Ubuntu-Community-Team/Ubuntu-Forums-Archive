---
title: "Installing windows along side Ubuntu"
date: 2016-01-09
forum: General Help
---

### Post by everytimeref on 2016-01-09
For a variety of reasons, (least of all fallout 4) I need a windows 10 installation. I'm a long term Ubuntu user (since Hardy) and haven't done this for a loooong time.

What I'm planning on is getting a new hard drive, disconnecting all my existing drives and installing Windows on the new one. Then plugging in the linux drives and errrrr somehow adding a line to Grub to connect to the windows 10 drive.

Is this sensible? if so can someone give me an idea of what the new Grub line should look like.

---

### Post by oldfred on 2016-01-10
If newer system, just be sure to have Windows installed in same boot mode, either UEFI or BIOS as Ubuntu. Make sure fast start up or the always on hibernation is off whether UEFI or BIOS boot.

Once all drives are connected run this:
sudo update-grub

Windows when installed will be first drive, better to keep it as first drive or plug it into first SATA port or port 0 on motherboard. Ubuntu uses UUIDs, so more flexible on which drive it boots from. 

If Ubuntu is UEFI, the UEFI NVRAM will forget entries from a drive that is disconnected and you may have to recreate them with efibootmgr from live installer. 
If BIOS you have to select whichever drive is Ubuntu drive to boot from in BIOS.

---

### Post by everytimeref on 2016-01-13
Thankyou, this is what I was looking for. (wish me luck, I'm going in!)

---

