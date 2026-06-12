---
title: "How to encrypt an USB stick for Linux and Windows (not WLAN)"
date: 2006-12-04
forum: General Help
---

### Post by fbn on 2006-12-04
Hi!

I'm owner of a 2GB USB stick and I want to protect my data on this device with encryption. The perfect solution would be to insert the stick, enter the correct password and have full access to the files which are all encrypted.

Most applications which encrypt data on USB sticks need administrative rights (at least once) on Windows, that's not possible for me (at school or internet cafe for example).

Is there any application or solution which can handle my requirements?

Regards,
  Frank

---

### Post by technodigifreak on 2006-12-04
as far as I know only TrueCrypt ([http://www.truecrypt.org/](http://www.truecrypt.org/)) will do what you want.  It has both Windows/Linux versions and both versions will fully inter-operate with the other versions.  The user manual will walk you through the process but the short version is:
A. Create 2 partitions on your thumb drive and format them both as FAT or vFat.  
B. Install TrueCrypt in 'traveller mode' (the manual tells you how) and then create an 'autorun.ini' file which points to your truecrypt executable on the first partition of your thumbdrive.  
C. Create a TrueCrypt volume in place of the second partition.
D. Install TrueCrypt for Linux on your Ubuntu machine and verify you can access data on that volume.

---

### Post by fbn on 2006-12-04
I already thought about TrueCrypt but this causes some issues:

> 
Q: Will I be able to mount my TrueCrypt partition/container on any computer?
A: TrueCrypt volumes are independent of the operating system. You will be able to mount your TrueCrypt volume on any computer on which you can run TrueCrypt (see also the question "Can I use TrueCrypt on Windows if I do not have administrator privileges?").

Q: Can I use TrueCrypt on Windows if I do not have administrator privileges?
A: Yes, but only after a system administrator installs TrueCrypt on the system (or after he or she gives you administrator privileges). The reason for that is that TrueCrypt needs a device driver to provide transparent on-the-fly encryption/decryption, and users without administrator privileges cannot install/start device drivers in Windows. After a system administrator installs TrueCrypt on the system, users without administrator privileges will be able to run TrueCrypt, mount/dismount any type of TrueCrypt volume, load/save data from/to it, and create file-hosted TrueCrypt volumes on the system. However, users without administrator privileges cannot encrypt/format partitions, cannot create NTFS volumes, cannot install/uninstall TrueCrypt, cannot change passwords/keyfiles for TrueCrypt partitions/devices, cannot backup/restore headers of TrueCrypt partitions/devices, and they cannot run TrueCrypt in 'traveller' mode.


I do not have administrative access to computers at school or internet cafe or office desktops.

Do you know of a solution for that?

Frank

---

### Post by technodigifreak on 2006-12-04
I was under the impression that even though you couldn't create a truecrypt volume you could mount an already existing one from within travel mode.  The only other option that would bypass administrative issues would be a live CD.  I think a live cd would probably be more of a hassle than you are looking for.  What about installing Ubuntu to the thumb drive and booting into it with True Crypt installed?  

I'm not sure this is a viable option as your drive may not have boot support, but it is certainly worth looking into.  I'll look into it further as well.

---

### Post by fbn on 2006-12-05
Booting from USB-Stick or CD-Rom is possible at school but then I'm unable to use the applications provided.
Also at work and other places this could be a impossible thing to do.
I'm wondering if nobody has ever done such a thing without administrative rights on Windows?

---

### Post by fbn on 2006-12-07
any news on your test?

---

