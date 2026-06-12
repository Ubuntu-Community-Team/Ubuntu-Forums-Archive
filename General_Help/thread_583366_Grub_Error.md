---
title: "Grub Error"
date: 2007-10-20
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2007-10-20
I have to hard drives on my computer, one with XP and one with 7.07. I formatted the 7.07 harddrive today to install it on my other computer, but now when i boot the now xp machine, i get Grub error  17, and i cant doa nything from there. 

How can i fix this so this computer will boot into Windows?

---

### Post by gm__ on 2007-10-20
Use Supergrubdisk , it solves the problem for me everytime i reinstall.

[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

---

### Post by HokeyFry on 2007-10-20
can you post the output of```
cat /boot/grub/menu.list
```

---

### Post by HokeyFry on 2007-10-20
wait i see what you are saying now, lemme get this straight...
your dual boot PC is now a windows only pc?

if this is the case the best bet is to reinstall the windows bootloader

---

### Post by s_h_a_d_o_w_s on 2007-10-20
Thanks for the replies :D

Yes now when i start the computer it loads grub (from where i have no clue) and i get error 17, how can i scrap grub completely and just use ntldr to boot windows like it would natively?

How can i restore ntldr?

---

### Post by HokeyFry on 2007-10-20
do you have a windows recovery cd?

---

### Post by s_h_a_d_o_w_s on 2007-10-20
I have the CD that installs Xp if that's what you mean :D

---

### Post by HokeyFry on 2007-10-20
alright heres what you do, boot up into the cd, go into the recovery console, and tpye in fixboot, then fixmbr

this should fix everything

---

