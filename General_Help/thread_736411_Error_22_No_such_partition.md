---
title: "Error 22: No such partition"
date: 2008-03-26
forum: General Help
---

### Post by Bertzored on 2008-03-26
The installetion in windows worked fine and also the installation in "ubuntu". But when I choose Ubuntu in the menu the second time I get:

[B]root (hd1,1) ubuntu/disks
Error 22: No such partition [/B]

Please help me! :(

---

### Post by Termy58 on 2008-03-26
It looks like your hard drive refused to create a new partition through some security/incompatibility.

Can you answer the following questions for the Devs

1. Operating System
2. Hard Drive
3. Any firewalls/security systems you have

---

### Post by Bertzored on 2008-03-26
Windows XP SP2
NTFS
COMODO Firewall and Antivirus

---

### Post by ago on 2008-03-26
edit c:\ubuntu\disks\boot\grub\menu.lst

replace (hd1,1) with (hd0,1)

---

### Post by Bertzored on 2008-03-27
> **ago said:**
> edit c:\ubuntu\disks\boot\grub\menu.lst

replace (hd1,1) with (hd0,1)
That did it. Thx!

---

### Post by ago on 2008-03-27
make sure you also replace # groot (hdX,Y)....

or menu.lst will revert to the old values on upgrade

---

### Post by D0R1AN on 2008-04-22
Right on, editing right in the command line fixed my problem too. Thanks dudes!

---

### Post by Xsnip3rX on 2008-05-01
Hi, i also get this error, only mine says root (hd1,4), so do i replace the 1 with a 0?

---

### Post by DaveBG on 2008-05-02
You can try (hd1,4) -> ()   

Yes only empty brackets. It did work for me too :) ( 10x to ago!)

---

### Post by ago on 2008-05-02
[https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230](https://wiki.ubuntu.com/WubiGuide#head-281e2c55090fcd96336e6fe3029fec5aede1a230)

---

