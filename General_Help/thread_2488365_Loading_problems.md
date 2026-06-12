---
title: "Loading problems"
date: 2023-07-03
forum: General Help
---

### Post by zz131rw on 2023-07-03
New to Ubuntu, and Linux in general.
So, I bought a refeb laptop with 22.04.2 LTS on it, problem was it had only 128 gb SSD
I made a backup stick & replaced the SSD with 1 tb SSD. 
loaded Ubuntu onto the 1 TB SSD & somehow also making the stick partitioned with Ubuntu
On booting I have to hit F12 & scroll to UEFI BOOT, Ubuntu (22.04.2 lts)
How can I get my laptop to automatically boot from UEFI?
Thank you for your time.

---

### Post by aljames2 on 2023-07-03
> **zz131rw said:**
> I made a backup stick & replaced the SSD with 1 tb SSD. 
loaded Ubuntu onto the 1 TB SSD & somehow also making the stick partitioned with Ubuntu

On booting I have to hit F12 & scroll to UEFI BOOT, Ubuntu (22.04.2 lts)
How can I get my laptop to automatically boot from UEFI?
Thank you for your time.

Hi zz131rw, welcome

If I understand you correctly, you used a USB stick to backup up the old 128gb SSD, is that correct?

Then you removed the 128gb SSD and replaced it with a new 1 TB SSD.  Nice so far.

However, did you leave the USB stick inserted while installing Ubuntu to your new SSD?  If so, that could be how your USB stick is now included in your Ubuntu installation ecosystem.  I usually do OS installs with only the target disk installed, this leaves out the possibility of overwriting something on another plugged in storage device.  Clarify this if we are misunderstanding..

Further, tell us how you prepared the new SSD for the ubuntu installation.  Did you create a GPT partition table on the device before installation?  GPT is used for UEFI boot mode.  If you happened to partition it Legacy then that would cause the system to not invoke UEFI boot.  Others here are more expert in fixing boot mode issues.

---

### Post by oldfred on 2023-07-03
What brand/model system?
Most but HP will let you change boot order with efibootmgr -o which grub uses when it installs.
man efibootmgr

But do you have system set to default boot in UEFI mode?

---

