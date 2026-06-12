---
title: "Can't boot after installing upgrading to 13.10"
date: 2013-10-18
forum: General Help
---

### Post by Alan_Furth on 2013-10-18
Hi all, I installed Ubuntu 13.04 a couple of days ago on a brand new laptop with Windows 8 on a dual boot. A few days later I eliminated Windows 8 altogether and everything seemed to be working perfectly fine until I upgraded to Ubuntu 13.10 and now my laptop just won't boot.
Ideally I'd like to at least be able to access to the data in my laptop to recoup some info I didn't back up (mainly the passwords stored in "Passwords and Keys" and the encrypted "Private" folder), but it wouldn't be a big deal for me to re-install Ubuntu 13.10 from scratch even if I loose that data, after all I am not sure I did a great job eliminating Windows 8 as the partitions of my hard drive look a bit chaotic to me. I am attaching a screenshot of how they look on Gparted in case you think it might help...
Thanks in advance!

---

### Post by oldfred on 2013-10-18
The msftres is from Windows. It shows error as it is supposed to be unformatted space, so gparted cannot see its format. It is tiny so it does not really matter.

If encrypted, you have to mount encrypted partition, or /home with passphrase. Otherwise the entire purpose of encryption is to prevent unauthorized access.
But I do not see an encrypted partition from full drive encryption and normally encrypted /home also has an encrypted swap that again gparted cannot see, so it shows an error on swap. Yours shows normally.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Alan_Furth on 2013-10-18
thanks oldfred, I'll start by creating the live USB with Boot-Repair and try it to see what happens!

---

### Post by Alan_Furth on 2013-10-19
The Boot-Repair worked perfectly, thanks again!

---

### Post by mörgæs on 2013-10-19
Please notice Oldfred's signature.

---

