---
title: "Entering encryption passphrase correctly makes drive disappear?"
date: 2015-08-11
forum: General Help
---

### Post by gammies on 2015-08-11
Relatively new Ubuntu user here.  Was having some issues during the bootup and tried running Boot repair.  After I finished running it and restarted to see if it worked it gave me an error something like "no bootmgr found" 

So I decided to reinstall Ubuntu on a different drive.  So now that I have a fresh install. which I was considering doing anyways, I have my old drive on the left hand side and it has a little padlock on it to symbolize it being encrypted.  When I click it asks for a passphrase.  No problem right?  Just enter the password and I will be able to view the contents.  Instead of giving me access to the drive, it simply disappears.  It still shows up when I run sudo parted -lbut I cannot access my old files.  

Thanks for reading, hope I can get this figured out.

---

### Post by frostschutz on 2015-08-11
Wild guess, but maybe you don't have a filesystem in that container but LVM. And if it's LVM, maybe you already have LVM in your running system, and both LVM's volume groups are named ubuntu-vg. And that wouldn't be a problem, except that LVM does not usually allow two volume groups of the same name, so you have to rename one.

To collect more information in the terminal, try 'sudo blkid', or 'sudo file -s -L /dev/mapper/*' after unlocking the device; if it's not unlocked, do it with 'sudo cryptsetup luksOpen /dev/thing luksthing' and then use file on /dev/mapper/luksthing to find out what's on it.

---

### Post by gammies on 2015-08-11
Ok, so after unlocking the drive and running sudo blkid it gives me this output.  Unfortunately, I have no idea how to interpret it.  

/dev/sda1: LABEL="SSD" UUID="5A92A33E92A31D8F" TYPE="ntfs" 
/dev/sda2: LABEL="2tb" UUID="4EDA5A31DA5A1615" TYPE="ntfs" 
/dev/sdb1: UUID="54cf1d89-d4bb-401e-b099-d401204aad50" TYPE="ext2" 
/dev/sdb5: UUID="63e1a84f-1e21-4b86-a07e-9f91176eb2b5" TYPE="crypto_LUKS" 
/dev/sdc1: UUID="0FF3-C685" TYPE="vfat" 
/dev/sdc2: UUID="f9586525-02e7-460c-8b2f-42dffe656c97" TYPE="ext2" 
/dev/sdc3: UUID="a57567c7-efaf-40b0-8849-64d5ea5a23cc" TYPE="crypto_LUKS" 
/dev/mapper/sdc3_crypt: UUID="cht6r3-jAv6-ZLIV-ba0b-uEin-fbsH-vsHU6B" TYPE="LVM2_member" 
/dev/mapper/ubuntu--vg-root: UUID="e71c4c1c-f02e-4937-92b7-9d27d4e0d50b" TYPE="ext4" 
/dev/mapper/ubuntu--vg-swap_1: UUID="e4b0edfc-0d7f-4f6b-a153-518cffa501b3" TYPE="swap" 
/dev/mapper/luks-63e1a84f-1e21-4b86-a07e-9f91176eb2b5: UUID="q5Ax0s-bd4r-Aey3-R51J-EnOl-xIgm-0HM28T" TYPE="LVM2_member" 


the SSD is the hd I'm trying to access (judging by volume size) but it only lets me access 76 items, totalling 15.4 MB out of 26 gb.  This is accessible before entering the key though.

---

### Post by frostschutz on 2015-08-11
You have two open crypt containers and LVM on both.

Next step, 'sudo vgdisplay'

---

### Post by gammies on 2015-08-11
you are right.  i need to change the volume group names.  i tried renaming the drives but it didn't work.  how do I change the volume group names?

---

### Post by frostschutz on 2015-08-11
sudo vgrename oldname newname

or in your case since the name isn't unique

sudo vgrename uuid newname

uuid should be displayed by vgdisplay

---

### Post by gammies on 2015-08-11
Thank you so much Frost!  :KS

---

