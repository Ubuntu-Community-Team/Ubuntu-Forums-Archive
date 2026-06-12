---
title: "Hard drive with full encryption showing errors."
date: 2013-05-16
forum: General Help
---

### Post by Wuggysback on 2013-05-16
I had an Ubuntu 12.10 installation with full drive encryption and I noticed that the hard drive was going bad according to S.M.A.R.T. at boot. I added another hard drive thinking that I would just transfer the files after the installation. I installed Backtrack 5 on the new hard drive feeling as if I would still have the boot options to choose which installation I would like to boot. Needless to say when the new install kicked in it never showed me my old hard drive with my precious data on it. I can see it in Gparted but it's locked with the encryption. Is there anyway I can possibly unlock the drive from my new installation or am I going to have to figure out another way to accomplish the data transfer. Any help would be greatly appreciated & thanks in advance!

---

### Post by carl4926 on 2013-05-16
You can't boot in to 12.10?
Even with a grub mod or tool like supergrubdisk?

---

### Post by moody_mark on 2013-05-16
You should have had to give a encryption passphrase when you first setup the encryption (usually), and you should be able to mount the directory using this passphrase and the tools with ecrypt-fs. Its not something I've done before but I do have a directory on my work machine which is encrypted which gets de-crypted on startup.

Have a look at this article, it might give you some pointers: [https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory)

---

### Post by sudodus on 2013-05-16
Welcome to the Ubuntu Forums :-)

Don't use the failing drive more than absolutely necessary until you have a cloned copy of it (or what can be cloned). The best thing would be to learn about ***ddrescue*** browsing the internet from another computer.

You can clone (the data on) the drive that is starting to fail with ddrescue to the new drive.

The info page is very good (several examples)

```
 info ddrescue
```

If you follow those instructions (maybe with some help from us at the Ubuntu Forums), you have a fair chance to succeed. For example, use a log file.

If you get no errors in the transfer, you can replace the failing drive with the new one and go.

If you get errors, use ddrescue to recover as much as possible. Probably there are only a few bad areas, and if you are lucky, the system will boot from other areas on the disk, and maybe only a single of a few data files are bad.

Good luck :-)

---

### Post by Wuggysback on 2013-05-16
Im looking into crypt setup right now but it's asking me to use a device name as an argument and the device doesn't have a name it's listed as /sda5. cryptsetup luksOpen /dev/sda5 is the command I tried to use and  #cryptsetup: luksOpen: requires    as arguments# is the output that it gave me. I feel so close lol.

---

### Post by mörgæs on 2013-05-16
Next time please use a more informative thread title.

---

