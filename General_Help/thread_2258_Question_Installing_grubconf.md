---
title: "Question: Installing grubconf"
date: 2004-10-26
forum: General Help
---

### Post by iminj on 2004-10-26
I'd like to install grubconf, as I understand it offers a GUI-based method to configure  grub. I'm a noob, and this is unfamiliar territory for me.

Here are the questions:

(1) Do I have to remove grub, or do I  just add grubconf? 

(2) Does grubconf go on the MBR .. or is there another default or preferred location ?

(2) I have 2 hard drives; grub, Windows,and the MBR are on the first drive, ubuntu is installed on the other. How do I ensure that grubconf gets installed on the MBR .. or linked to grub on the MBR, and doesn't create a 2nd MBR on the ubuntu drive?

Thnx
iminj

---

### Post by iminj on 2004-10-27
I found grubconf in one of the 2 unsupported file repositories, ( which I had to activate and connect to first). I installed it ( there were NO options), and it works like a charm. Once installed, you simply enter "grubconf" in a terminal as a root user, and the gui file opens. Easy.

ubuntu did warn me about the file being unsupported, so I don't know if everyone will be succesful with this file.

---

