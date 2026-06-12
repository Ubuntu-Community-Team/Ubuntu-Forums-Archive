---
title: "can't locate a file that I know is there"
date: 2007-11-17
forum: General Help
---

### Post by faust99 on 2007-11-17
I created a backup file of /boot/grub/menu.lst called /boot/grub.menu.lst.bkp, but none of the commands (locate, find, whereis) can find it. I know it is there, because I can see it when I go to that directory via the terminal. This is intriguing. Does anybody know why none of the search commands can find it??:confused:

---

### Post by taurus on 2007-11-17
```
sudo ls -la /boot/grub
```

p.s.  Is it **/boot/grub.menu.lst.bkp** or **/boot/grub/menu.lst.bkp**?

---

### Post by faust99 on 2007-11-17
Thank you. That shows me the file, assuming I know where roughly where it is, in the first place. But what if I did not know that?

---

### Post by taurus on 2007-11-17
```
sudo find / -name menu* -print
```

---

### Post by faust99 on 2007-11-17
Great Taurus, that worked. Thank you.  By the way, the file is /boot/grub/menu.lst.bkp. 

But since 'locate' was able to find /boot/grub/menu.lst, why not boot/grub/menu.lst.bkp, I wonder??

---

### Post by meierfra on 2007-11-17
> But since 'locate' was able to find /boot/grub/menu.lst, why not boot/grub/menu.lst.bkp, I wonder??

Did you create "/boot/grub/menu.lst.bkp" recently?  locate only finds files in its data base, which is updated periodically.  But you can run "sudo updatedb" to update it before your search (but it takes a while)

---

