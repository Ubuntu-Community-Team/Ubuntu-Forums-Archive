---
title: "Ddrescue issue"
date: 2017-09-17
forum: General Help
---

### Post by Evil Wayz on 2017-09-17
I was using ddreascue with a 2tb being rescued to a 4tb and now my computer is completely full.  I can't find out where hte 15gbs of space i had yesterday went.  Disk-analyer doesn't seem to show anything.

I had this happen once when i didn't correctly choose hte right disk in testdisk.

I also ran test disk this same day.

Anyone come across this before.

I ma running Xubuntu 17.04 with the standard kernel.

---

### Post by VMC on 2017-09-18
'ncdu' is a better choice too see what usage you have. Run it from terminal on your '/' root partition (ncdu /).

---

### Post by Evil Wayz on 2017-09-26
I can't even login.  I type in my password and it kicks me back to the login screen.  I tried deleting stuff using a live usb stick but nothing deletes.  And for some reason it wont let me turn on multiverse so i can install ncdu.

Im really screwed here and could use some help.

---

### Post by VMC on 2017-09-26
I don't know what 'hte' is. Try booting with a live ubuntu disk, then install 'ncdu' then point it to the partition in question.

---

### Post by Evil Wayz on 2017-09-26
"hte" is the,  misspelled. 
Live USB doesn't have ncdu,  won't let me install it,  when add universe report,  server error when updating.       
Assuming I can get ncdu to work,  I don't know where to point it,  and I don't know how to get permission to delete.   I tried deleting any large file using nautilus as root but I got as far as deleting but I don't know how to empty trash as root.

EDIT:

I have successfully installed ncdu and found the offending file, which is once again a testdisk.log that bloated to 44 gb.  How do I delete it within a live environment?

---

### Post by VMC on 2017-09-26
from live: sudo rm /<file location>/testdisk.log

---

### Post by Evil Wayz on 2017-09-26
That did the trick, thanks.

---

### Post by VMC on 2017-09-27
Under "Thread Tools" , please mark as solved, if you satisfied.

---

