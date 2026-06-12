---
title: "Updates under hardy impossible"
date: 2008-05-09
forum: General Help
---

### Post by njb on 2008-05-09
I have installed hardy in my PC desktop edition, x86 with live cd of 24/04/2008.
I have notification of 57 updates but when i run the updates it goes to no end.
and in the other side, my console can't turn to sudo mode !!
Ot gives me error message : "cant resolve hostname.

please , is there a new iso of hardy, i can download that integrate the new updates that have been done untill now 


thank you

:lolflag:

NjB

---

### Post by davidpbrown on 2008-05-09
Not sure if this is the best solution but it worked for me.

sudo gedit /etc/hosts
and add .local to your PC's name. Then try update manager/synaptic again.

Whether that should be changed back I don't know..


!Sorry just read you can't sudo.. so that won't work.

---

### Post by kpkeerthi on 2008-05-09
Use **Recovery Mode** from GRUB menu and edit your /etc/hosts file per recommendations  [here]("http://ubuntuforums.org/showthread.php?t=3407")

* sudo is not required in recovery mode and you may use **nano** to edit the file.

---

