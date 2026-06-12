---
title: "Live USB &quot;BOOT ERROR&quot;"
date: 2007-12-29
forum: General Help
---

### Post by Ioky on 2007-12-29
I tried to install linux in my 8GB USB drive, the installation ran pretty smooth, however, when I try to boot from it, it say "BOOT ERROR" Just this, but nothing else, I have no idea which part have went wrong. I wonder, did any one try this before, or run into the same problem as me.

Thanks

---

### Post by ramasan on 2008-01-22
Same problem here -

8GB Corsair Flash Voyager.

Followed directions pretty closely - according to wiki and according to pendrivelinux.com

"Boot error" every time.

I saw something about sector or cluster size on 2GB USB keys and a fairly terse ' thats the way it is and there is no plans to fix it' post on a mailing list.

---

### Post by wolfen69 on 2008-01-22
try this: If your having trouble getting Ubuntu to boot, your memory stick may have a corrupted MBR. To repair the MBR of your USB device, at the terminal type sudo apt-get install lilo then type lilo -M /dev/sdx (replacing x with the letter of your flash device)

---

### Post by ramasan on 2008-01-22
> **wolfen69 said:**
> try this: If your having trouble getting Ubuntu to boot, your memory stick may have a corrupted MBR. To repair the MBR of your USB device, at the terminal type sudo apt-get install lilo then type lilo -M /dev/sdx (replacing x with the letter of your flash device)

i had tried that already.  i didnt get an error when i typed the command in, rebooted, same issue.

---

