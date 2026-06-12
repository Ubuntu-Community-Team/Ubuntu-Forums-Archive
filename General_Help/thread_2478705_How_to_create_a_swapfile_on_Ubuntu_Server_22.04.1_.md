---
title: "How to create a swapfile on Ubuntu Server 22.04.1 LTS 32bit Raspberry Pi"
date: 2022-09-02
forum: General Help
---

### Post by us-palermo on 2022-09-02
HI,

I currently have a Raspberry Pi 2 with 1 gig of ram and would like to add a swapfile to my existing setup.

OS: Ubuntu Server 22.04.1 LTS 32 bit
storage: 128 gb Sandisk flash & a USB HDD sda1 which already has files on it and formatted with ext4 already.

OS is hosted on the Sandisk and the USB HDD SDA1 is for storage(samba)

I would like the swap file to be on the existing USB HDD sda1 without erasing any files on that drive.

any help would be appreciated.

Thank you.

---

### Post by TheFu on 2022-09-02
mkswap to create the block file.
Then add it to the fstab like any other swap.  Use sudoedit to edit the fstab.

---

### Post by us-palermo on 2022-09-02
I did that however my swap file is on my micro sd SanDisk flash drive, I want the swap to be on the USB attached drive I have already in place which is mounted

---

### Post by us-palermo on 2022-09-02
Just to make sure in the fstab do I put this to identify my HHD for the swap

/swapfile UUID="MY HARDRIVE IDXXXXXXX" none swap defaults 0 0

save fstab
then swapoff and swap on for it to take affect?

---

### Post by us-palermo on 2022-09-03
well the solution for me was to activate the zram on the raspberry pi and forget about the swap file idea, it seems to have improved the performance :)

---

### Post by TheFu on 2022-09-03
> **us-palermo said:**
> Just to make sure in the fstab do I put this to identify my HHD for the swap

/swapfile UUID="MY HARDRIVE IDXXXXXXX" none swap defaults 0 0

save fstab
then swapoff and swap on for it to take affect?

/swapfile will be in /.  I thought you wanted it on the mounted USB storage?  That is just a file path to the swapfile you created with the mkswap cmd.  Don't know that using USB is a good idea for that purpose.  USB devices lost connectivity and doing that to swap would likely crash the system, but whatever. It's yours, not mine.  Having swap on a microsd/SD will be bad for that storage device's limited write abilities.  This is part of the reason that raspberry pi systems aren't a good idea for normal server stuff.  There are embedded platforms with slightly higher cost, much more CPU, fanless, and mSATA support (and internal SATA connections) that aren't THAT much more power hungry for when people want a fanless, low-power server.

---

