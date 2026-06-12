---
title: "Boot Screen Help"
date: 2007-11-09
forum: General Help
---

### Post by anon2243 on 2007-11-09
if a previous thread you suggested editing the usplash.conf file to 1024x 768 and then running the following command

sudo update-initramfs -u -k $(uname -r) 

but i can't get this command to run it says warning /boot is ro mounted...is this because of wubi...is there any way around this?

---

### Post by crjackson on 2007-11-09
> **anon2243 said:**
> if a previous thread you suggested editing the usplash.conf file to 1024x 768 and then running the following command

sudo update-initramfs -u -k $(uname -r) 

but i can't get this command to run it says warning /boot is ro mounted...is this because of wubi...is there any way around this?

I'm very sorry, I don't recall suggesting that to you...

---

### Post by anon2243 on 2007-11-09
sorry i meant 'ago'...but is there any way to update the usplash.conf change that i made?

---

### Post by ago on 2007-11-09
Boot should be mounted r/w, double check that. It should be mount binded to /host/ubuntu/disks/boot

---

### Post by anon2243 on 2007-11-10
I checked the menu.lst file an it shows the kernal being loaded as ro...does that matter?

Otherwise I'm afraid I don't know how to check the bindngs....can you provide any additional commands i can run?  This is a fresh install and I'm getting this error...

---

### Post by anon2243 on 2007-11-10
update: i ran from terminal the mount command and it said that /host/.../boot is (rw) so why is the command failing...

however,  mkinitramfs -o /boot/initrd.img-`uname -r` worked great!

---

