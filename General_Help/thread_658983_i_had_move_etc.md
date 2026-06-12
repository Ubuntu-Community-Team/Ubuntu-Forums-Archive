---
title: "i had move /etc"
date: 2008-01-05
forum: General Help
---

### Post by jezu00 on 2008-01-05
Hello i had move /etc of system because what we really wanted was copied and now ubuntu not boot. I am trying to enter a livecd but when it comes to copying puts me: sudo: uid 999 doest not exist in the passwd file!

What i can do?I need to fix it because I have all my things Configured
i hope yours answer.
PD: sorry for my english

EDITED: 	
What happen if they lose install above all driver and etc.? Is there a way to install only that?

---

### Post by cmnorton on 2008-01-05
I don't know whether a symbolic link will work or not, but you could try it.
 
You would need to know the exact path to which you moved /etc.

Then ln -s /new-path-to-which-you-moved-etc /etc

If that doesn't work, you'll have to move /etc back, which would probably be the best thing to do anyway. Everything in the world is configured out of /etc. not to mentioned /etc/init.d, where the daemons are launched.

---

### Post by jezu00 on 2008-01-05
in the linking operation no permitted:(
second part i don't understand what i do? please can you repeat with some of intruntions pls

---

### Post by taurus on 2008-01-05
Where did you move /etc on your system to?  Maybe you can boot from the LiveCD, mount your harddrive, and _move_ it back.

---

### Post by jezu00 on 2008-01-05
i move /etc in hard disk portable but when i boot with livecd i don't permise for move back said:
sudo: uid 999 does not exist in the passwd file!

---

### Post by taurus on 2008-01-05
What partition on your harddrive is /?  You need to mount that partition and your external drive while running from the LiveCD.  Then, see if you can copy /etc from your external drive back to your harddrive.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by jezu00 on 2008-01-05
when i write sudo "with something" in the terminal said:
sudo: uid 999 does not exist in the passwd file!

---

### Post by taurus on 2008-01-05
A complete command that you tried to run would be nice?  Were you running from the LiveCD?

---

### Post by jezu00 on 2008-01-05
yes when i running with livecd. my system not boot

what happen if i installa new ubuntu? i lost my drivers?

---

### Post by taurus on 2008-01-05
You mean your machine wont boot from the CD?

If you reinstall and reformat your partitions, you have to reinstall all your drivers again.

---

### Post by jezu00 on 2008-01-05
thanks for your time but i will go to reinstal all...

---

