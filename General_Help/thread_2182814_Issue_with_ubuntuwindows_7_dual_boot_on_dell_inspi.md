---
title: "Issue with ubuntu/windows 7 dual boot on dell inspiron n5110"
date: 2013-10-22
forum: General Help
---

### Post by Omar_Bakir on 2013-10-22
Hello everyone! I've been using ubuntu for about a month and a half now but recently I've been having issues on startup. I get the "attempting to read or write outside of disk 'hd0'" error followed by a grub rescue prompt. I tried running boot repair and that fixed it for a few days but the problem has reappeared. This is the url I got from boot repair:

[http://paste.ubuntu.com/6261224/](http://paste.ubuntu.com/6261224/)

I'd appreciate any help I can get as I use ubuntu for my Computer Architecture class and it would be a problem if I don't have a working computer. Thanks in advance!

---

### Post by oldfred on 2013-10-22
Welcome to the forums.

I do not really see anything wrong.
It does look like you have Windows hibernated. That can cause Windows issues. Best not to hibernate when dual booting.

Some BIOS seem to have issues with grub & kernel files far into drive. 
Is BIOS set for AHCI? If not you can try changing it. You may need to install AHCI drivers in Windows first to get it to work with AHCI.

---

