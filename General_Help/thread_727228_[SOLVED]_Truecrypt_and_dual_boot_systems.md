---
title: "[SOLVED] Truecrypt and dual boot systems"
date: 2008-03-17
forum: General Help
---

### Post by samurailink3 on 2008-03-17
Does anyone have a hold-my-hand style tutorial for encrypting the entire drive through truecrypt? I've got a dual boot xp system, and I'm pretty sure I'll have to move grub (I believe it is in the MBR currently, and truecrypt needs to install a boot loader [is this correct??]). How would I do this without hosing grub? I've been looking at this for some time now, but I don't want to hose my system  . Thanks for the help!

*Note* This was also a thread in the 'Security Discussions', but I'm not sure this was the best place for it. Thanks for understanding!

---

### Post by markharding557 on 2008-03-17
don't think you can encrypt an entire drive with an o/s on it with truecrypt because true crypt would have to running in order to acess it.
you could have an encrpted linux partition using the ubuntu alternate installer.
this has a text installer which has options for creating a lvm partition and encrypting it

---

### Post by bodhi.zazen on 2008-03-17
The installer on the alternate CD is not so intuitive, but it will do the job using LUKS.

Here is a brief how-to : [http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html](http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html)

This method will create a /boot partition with grub which will boot windows and ubuntu.

There will be a second partition with your crypt.

---

### Post by samurailink3 on 2008-03-18
Ok, cool! Is this a pretty easy procedure that you know of, I'll try it out in the mean time! Will this automatically move grub? Or will I have to do this manually? Or will I use the truecrypt loader? In which case how can I edit it after a kernel update to still access my windows partition. 
Thanks a ton, I'm learning a lot already!

Oh yea, I did know about the crypt on the alt-ubuntu cd, but I'm looking for a way to use truecrypt to encode the entire hard drive (as I do have vast amounts of data already on here)? Is this possible as of yet?

---

### Post by markharding557 on 2008-03-18
an easier solution is to make a separate partition,encrypt this with truecrypt and then put all your sensitive data in it.
you would not have to carry out any major installations etc this way

---

### Post by bodhi.zazen on 2008-03-18
I am not sure of TrueCrypt, but LUKS in Linux is destructive. This means you will lose all your data, so back up anything you want to keep.

LUKS will not encrypt your Windows installation. This default is to encrypt the entire HD, which would destroy your windows installation. Set up your partitions before you install Ubuntu and read the link i gave you. To perform an encrypted installation of Ubuntu you will need a 512 Mb /boot partition and a separate partition for encryption. The encrypted partition will contain BOTH your swap and root partition.

The alternate CD should set up GRUB automatically to boot either Windows or Ubuntu.

---

### Post by samurailink3 on 2008-03-19
Ok, I'll look into full drive encryption when I reinstall next (might be around 8.04, as I'm kind of security-oriented). Thanks for all the help!!

---

