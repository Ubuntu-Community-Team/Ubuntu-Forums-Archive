---
title: "SSD Trim broken 13.04"
date: 2013-04-26
forum: General Help
---

### Post by flashnpan on 2013-04-26
I just did a fresh install of 13.04. I am dual booting with Windows 8. I was dual booting 12.10 and Win 8 before the new install with no problems on my Samsung 840 ssd. Now the sudo fstrim -v / is broke. I get this return from the terminal "fstrim: /: FITRIM ioctl failed: Input/output error". I have ran fsck it came up clean. Trim still works on the Windows side. Any ideas

---

### Post by markbl on 2013-04-27
Not much help but fyi, my fresh install of 13.04-amd64 works fine using "fstrim -v /" on my Samsung 830 ssd. No difference to my 12.10 install.

---

### Post by flashnpan on 2013-04-30
Thanks for the reply. I just added the discard mount option to etc/fstab. It seemed to be working without any noticable slow down as others have had. Maybe I won't need trim.

---

### Post by Slim Odds on 2013-04-30
I would highly recommend running a daily CRON job instead. It's far more efficient. Trimming after every delete is overkill and will slow your system down even if you don't notice it.

---

### Post by pqwoerituytrueiwoq on 2013-04-30
> **Slim Odds said:**
> I would highly recommend running a daily CRON job instead. It's far more efficient. Trimming after every delete is overkill and will slow your system down even if you don't notice it.What if your ssd is a boot drive?
[LIST]
[*]/ on SSD
[*]/home on HDD
[*]/root on HDD
[*]/var on HDD
[*]/tmp on RAM
[/LIST]

---

### Post by Slim Odds on 2013-04-30
> **pqwoerituytrueiwoq said:**
> What if your ssd is a boot drive?
[LIST]
[*]/ on SSD 
[*]/home on HDD 
[*]/root on HDD 
[*]/var on HDD 
[*]/tmp on RAM 
[/LIST]

It works just fine.

I have a daily CRON job that runs trim on / and /home which are both on the SSD

P.S. Trim does not actually affect the file system. It is a way to communication file system information down to the drive itself (internals).

---

### Post by flashnpan on 2013-04-30
If fstrim -v / isn't working, I don't think cron is going to work . If no one has a fix I think I will try to reinstall. I don't like using the discard option, even if seems fine.

---

### Post by lisati on 2013-04-30
*Thread moved to **General Help**.*

13.04 isn't the current "+1" anymore.....

---

### Post by pqwoerituytrueiwoq on 2013-04-30
Can the OP check his/her S.M.A.R.T data using [gsmartcontrol](apt:gsmartcontrol)? you may need to RMA the drive
you need to have your sata controller set for AHCI mode for trim to work

---

### Post by flashnpan on 2013-04-30
Maybe that's it. My bios doesn't have AHCI mode.Trim worked in 12.10 without AHCI. Does 13.04 require it?

---

### Post by pqwoerituytrueiwoq on 2013-04-30
as far as i know trim does not work with ide mode, can you run a bios update?

---

