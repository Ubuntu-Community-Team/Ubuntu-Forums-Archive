---
title: "Have I been grubbed?"
date: 2007-01-15
forum: General Help
---

### Post by dawhistler on 2007-01-15
Hello All,

I just ran into an issue with grub...I cannot boot to it or from it.
I am running Dapper 6.06 and found that a bunch of Icons vanished...I re booted and now I get error 15....AAAAAHHHHHHH.

I am NOT dual booting, using xp or anyother os...

Any ideas?



mas

---

### Post by meng on 2007-01-15
Did you "do" anything you suspect might have caused this?

---

### Post by dawhistler on 2007-01-15
But of course....;) 

I was ridding myself of uneeded programs and adding others.  The only thing I removed was the python programmin prog.  I was under the impression that it was an add on and could be removed safely.


mas

---

### Post by meng on 2007-01-15
Perhaps the quickest option is just to reinstall Ubuntu??
Unless you're strapped for space, I wouldn't recommend removing much from the default install (sure it's a little bloated, but not that much) and I certainly wouldn't recommend taking out Python, since there are some neat applications which use Python. That doesn't explain why grub died though.

---

### Post by dawhistler on 2007-01-15
is there a method to install Dapper and be able to access previous programs?
I really dont want to throw everything out

---

### Post by Ramses de Norre on 2007-01-15
You should first try to fix it before reinstalling it.
Have you already tried booting a live disc? You can try this:
```

sudo mkdir /media/root
sudo mount -t ext3 /dev/xxx / /media/root  ##fill in the right root partition
sudo chroot /media/root
sudo aptitude update && sudo aptitude upgrade && sudo aptitude install ubuntu-desktop linux-generic
sudo grub
root (hd0,0)   ##fill in your / partition (containing /boot), start counting from 0 for device and partition
setup (hd0)   ##install to mbr
quit

```
Be certain to do the aptitude stuff to get python back (necessary for many ubuntu apps) and to make sure your kernel is ok (grub error 15 can be caused by missing kernel image).

---

### Post by dawhistler on 2007-01-15
I have booted to a live disc and have pulled up terminal...but after entering the mount -t command it gives me notes on how to proporly use the mount command.
So far the  -t switch is  :ordinary mount command

The command is mount [ -t fstype] something somewhere....this looks like what you suggested 


My brain is starting to fog over like the windshield of a Ford Pinto....:p

---

