---
title: "Issues with Encryption (Full Disk)"
date: 2013-02-09
forum: General Help
---

### Post by walterkay on 2013-02-09
Sorry if this post is too long or this is the wrong section, I am a new member here. However I've been using Ubuntu for the past few years and it's one of my two favorite linux distributions.


The problem I am having is with Ubuntu's encryption. I am pleased that the new 12.10 installer has an option to encrypt the installation. I selected the encryption (I did not select LVM I prefer ext4.) and~ I also checked the "Encrypt entire disk with free space" as I prefer everything to be encrypted.


Now onto the problem. Everything went fine except the install took only about ~15 minutes. I'm sure  thats a good thing but I know for sure that it is impossible to encrypt an entire 500GB hard drive in fifteen minutes. I also reran the installer and nowhere did it even say "encrypting" during the installation. However when the PC starts up it asks for an encryption password first so it looks like the encryption is enabled, but that really is impossible.


Posting here is a last resort, as I try not the burden the Ubuntu community since I already have a great product for free. However, I tried every fix that I could think of and nothing helped. I re-ran the installer with the LVM option enabled, nothing changed everything was exactly as before. Now, the laptop I used uses EFI boot, there is no way to change that (Asus doesn't list the option in the BIOS) so I thought maybe that was the problem. Apparantly it isn't because I have a 2010 Gateway laptop on which I ran the installation and received the same results. I also ran the installation both with the ext4 and then the LVM partitioning. 


The strange thing is that everything looks fine in the disks section, you can't even tell that the laptop isn't truly encrypted. Had I not been experienced with encryption, I would have brushed this issue off. However as an experienced user of Truecrypt, Symatec Encryption, and Bitlocker (with and without TPM) I am certain that such fast encryption is impossible. I prefer to stick with Ubuntu's encryption rather than other linux encryption software like luks (or whatever it's called). Please help me figure this thing out, I think I am missing an obvious step somewhere.



Thank you.

---

### Post by alphacrucis2 on 2013-02-09
One thing you could try is boot up using the live CD and select "try ubuntu". If it can read the hd then it is not encrypted.

---

