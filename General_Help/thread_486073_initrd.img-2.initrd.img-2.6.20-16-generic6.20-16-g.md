---
title: "initrd.img-2.initrd.img-2.6.20-16-generic6.20-16-generic"
date: 2007-06-27
forum: General Help
---

### Post by SteveF on 2007-06-27
Hi,

I'm hoping someone can give me information about this file.  I've been having cd burning issues which I think are related to the new use of scd0 as the device.  At one point, it started to work, but then it failed again.  Since the kernel version did not change (vmlinuz-2.6.20-16-generic) I could not go back to the prior version.

I noticed in my /boot folder that the file initrd.img-2.6.20-16-generic had a backup file.  The dates corresponded with when the drive worked for a short period.  I have copied the bak version to the normal version and restarted.

As I hoped, the cdrom device was now back to hdc (the change also affected all hard drives changing them back to hda and hdb).

My cd burning now works.

I know this is temporary and that Ubuntu is moving to using SCSI names, but at least I have a working cd burner.

Now for my question :)

Will copying the file initrd.img-2.6.20-16-generic now cause a problem since it does not match up to the actual deployed kernel?

Steve

---

### Post by bierholen on 2007-07-29
Are you still working with the restored kernel 2.6.20-16.28? Did you encounter any problems?

---

### Post by bierholen on 2007-07-31
I just followed your instructions but copying back the initrd.img-2.6.20-16-generic.bak file did not change anything:-( Still having the same problem.

---

### Post by bogolisk on 2007-07-31
> **SteveF said:**
> Hi,

I'm hoping someone can give me information about this file.  I've been having cd burning issues which I think are related to the new use of scd0 as the device.  At one point, it started to work, but then it failed again.  Since the kernel version did not change (vmlinuz-2.6.20-16-generic) I could not go back to the prior version.

I noticed in my /boot folder that the file initrd.img-2.6.20-16-generic had a backup file.  The dates corresponded with when the drive worked for a short period.  I have copied the bak version to the normal version and restarted.

As I hoped, the cdrom device was now back to hdc (the change also affected all hard drives changing them back to hda and hdb).

My cd burning now works.

I know this is temporary and that Ubuntu is moving to using SCSI names, but at least I have a working cd burner.

Now for my question :)

Will copying the file initrd.img-2.6.20-16-generic now cause a problem since it does not match up to the actual deployed kernel?

Steve

I'd recommend you not play with those files since you're unfamiliar with them. The backup was there because you installed some extra drivers. usually during postinstall, update-initramfs will add the new driver(s) from /lib/module/.... into the initrd file (the real root file system) to make it available before the user root filesystem was mounted.

As for dvd burning issues, it's an unsolved kernel bug in 2.6.20 and 2.6.21. Some ppl said it's gone with 2.6.22 but it's might be just hiding somewhere. 2.6.20 is crappy but they made it the production kernel for feisty.  We're stuck with it unless they backported 2.6.22 to feisty.

---

