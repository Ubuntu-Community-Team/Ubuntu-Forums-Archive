---
title: "cannot mount hard disk"
date: 2008-05-06
forum: General Help
---

### Post by nimila on 2008-05-06
hi all,

just upgraded my ubuntu7.10 to 8.04 via add/remove manager. previous version all were working fine, but now one of hard disk in ntfs format cannot be seen/mount. in the gpart i can see it but in the computers folder it is not visible. booting through ubuntu cd all seems to be okay.

my numeric keypad also doesnt work.

any ideas. ?

just switch permanently to ubuntu from windows for the last 5 months now.

---

### Post by Damanther on 2008-05-06
What do you get with 'fdisk -l' and we'll see if we can figure it out.

For the number pad, did you make sure numlock was on?

---

### Post by nimila on 2008-05-10
the numlock key pad was sure on

a litle bit dumb in command line in the terminal, but i didnt get anything after typing "fdisk -l". 

just realized this though, my hard disk is identified as 'sda' through to 'sdc', but it is just an ide disk and from the manual it should be hda to hdc instead.

---

