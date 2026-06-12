---
title: "Configuring initramfs (RAID on top of Encryption (not vice versa))"
date: 2017-04-21
forum: General Help
---

### Post by jrdbrndt on 2017-04-21
I have two disks that I would like to stripe with RAID0 (using mdadm)  and encrypt the data (using LUKS). I also have another small  unencrypted disk to use for the boot partition. I understand that the  conventional way of doing this is to use mdadm to create the array --  say, /dev/md0 -- then use cryptsetup to encrypt md0. When I do this,  everything goes swimmingly. What I am experimenting with now is the  reverse of that... encrypt /dev/sdb and /dev/sdc, then create the array  using the encrypted volumes.

However, this presents some  interesting problems during boot. The initramfs attempts to build the  array first, before checking /etc/crypttab, and it can't assemble it, as  it can't find the metadata.

Now that you are aware of what I'm  trying to do, my basic question is: How can I force the initramfs to  check the crypttab file before the mdadm file? I'm sure this will just  come down to changing "10-mdadm.conf" and "20-crypt.conf" to  "20-mdadm.conf" and "10-crypt.conf", or something like that, I just have  no idea where to start looking as I've never played around with  initramfs-tools before.

Thanks in advance!

---

