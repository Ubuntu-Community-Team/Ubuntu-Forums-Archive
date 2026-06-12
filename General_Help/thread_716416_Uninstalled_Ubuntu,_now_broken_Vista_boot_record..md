---
title: "Uninstalled Ubuntu, now broken Vista boot record."
date: 2008-03-05
forum: General Help
---

### Post by banashe on 2008-03-05
I've searched a few other posts related to the subject and im trying to find a quick fix (short of reinstalling Ubuntu, booting into it, and modifying GRUB.

I have a Vista Business/Ubuntu 7.10 dual boot system. I was booted into windows when the thought hit me that I wanted to reinstall ubuntu from scratch. So (stupidly) formatted the partition from within windows.

This mistake obviously broke my MBR, as all GRUB info was on that partition.

I managed to find the one livecd I had lying around (Kubuntu 7.10) and downloaded ms-sys through apt-get, ran it to try and fix my MBR. It gave me a message (forgot it by now) implying that nothing was wrong, it detected an x86 boot record on that given partition.

Next, I used the Vista DVD image I had to see if i could repair it, but the repair tools on it couldn't find an error (only one of the wizards seemed to apply to my situation, and it found nothing).

Can anyone suggest anything that might work that wont involve reinstalling ubuntu (or vista for that matter) and manually configuring GRUB so I could boot back into vista? I'd like to get Vista as a single-boot on the system for now.

Thanks.

---

### Post by banashe on 2008-03-05
None of the wizards on the vista install dvd worked.

However, googled further, found out I needed to go into the command prompt through hte vista dvd and input:
Bootrec.exe /FixMbr

Rebooted, problem fixed.

---

### Post by Laughed on 2008-03-06
Glad you were able to solve your problem and share that here with us. I am sure other users will find this helpful.

---

