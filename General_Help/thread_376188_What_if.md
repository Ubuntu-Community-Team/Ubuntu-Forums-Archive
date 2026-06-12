---
title: "What if?"
date: 2007-03-04
forum: General Help
---

### Post by sdmike on 2007-03-04
I have two harddrives. One has linux and the other has windows. They are both SATAs.

My windows hard drive needs to be formatted. 

What if I format the windows harddrive and grub gets deleted.

How can I get grub back so I can use my linux harddrive?

Thank you for the help,
Mike

---

### Post by happyface_0 on 2007-03-04
If you have a floppy drive I believe you can add a grub installer to it.

Just put grub on a floppy before hand so you won't need to worry about the removal of grub.

---

### Post by Ocxic on 2007-03-04
or just unplugg your ubuntu drive  b4 the install and plug it back in when your done installing windows

---

### Post by sdmike on 2007-03-04
Too late I already wiped windows out and reinstalled it. So I no longer have grub. So how do I put grub on a floppy and reinstall it?

---

### Post by sdmike on 2007-03-05
I used the super grub cd and it gave me an error 15.

So what should I do now?

---

### Post by Ramses de Norre on 2007-03-05
Boot up a live cd and run these:
```

sudo -s
mkdir /media/root
mount /dev/??? /media/root -t ext3 -o rw
chroot /media/root
grub
root (hd?,?)
setup (hd0)
quit
update-grub
init 6

```
In the mount line you need to specify the device and partition for your ubuntu / (eg. sda3 here).
In the root line you need to do this again (assuming you don't have a separate /boot/ partition) but use only numbers counting from zero, so sda3 is (hd0,2) 0 because of the 'a' and 2 because of the '3'.

---

