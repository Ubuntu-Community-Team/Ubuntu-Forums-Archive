---
title: "SOS.....recovery file"
date: 2006-10-12
forum: General Help
---

### Post by wuj15 on 2006-10-12
Hi,
i am a newbie in using Ubuntu. I really love the the OS, but i am having some problem rite now. I recently follow a HOW-to thread to install XGL (correct me if i am wrong, the problem that make the 3D desktop), while i am installing that i came across the ubuntu configuation setup. I think i screw up some of the setting there. Now i can't even log in after the reboot. I just hear a beep after i key in the user:pass. And it will just go back to the login page. I have some really important files that i need to hand it to my boss tmr. Anyone can help me out.....thank you in advance....

---

### Post by encompass on 2006-10-12
What ever file you need you can still get it... but as for your configuration... I would recommend looking at where you made the mistake, or restoring all the backup config files you made.  XGL is not for work evironments yet.
To login to your computer from text mode, press cntrl alt and F1 then login... from there you can copy the file where you want.  Even email it.  IF you need to use the web try w3m.  But your going to feel pretty powerless, I don't think your used to that environment.
Does this computer have a direct connection to the internet?  Or is it on a network?
You could install an open ssh server in text mode... then from another computer on your network use winscp to retrieve the file and give it to your boss. :)

---

### Post by anaconda on 2006-10-12
You can rescue files with the liveCD, or you can select "recovery mode" from grub to boot to your system, take backups, and try to fix your problem..

---

### Post by encompass on 2006-10-12
OH yeah... duh... I forgot all about the live cd.  Thanks man.

---

