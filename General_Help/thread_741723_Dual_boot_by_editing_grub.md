---
title: "Dual boot by editing grub"
date: 2008-04-01
forum: General Help
---

### Post by kingleer on 2008-04-01
I've got Ubuntu 7.10 (64 bit) successfully installed on my computer. I have a second OS that I installed before I installed Ubuntu. 

Grub won't recognize it.  How do I edit Grub in Ubuntu so that I get a boot menu at start up asking me to choose which operating system to boot? 

Thanks.

---

### Post by angry_johnnie on 2008-04-01
Well, it pretty much depends on what the other OS is.

But, basically, you just have to edit /boot/grub/menu.lst
When you open the file, it will even give you examples on how to edit it.  Here's a couple:



 title		Windows 95/98/NT/2000
 root		(hd0,0)
 makeactive
 chainloader	+1

 title		Linux
 root		(hd0,1)
 kernel	                /vmlinuz root=/dev/hda2 ro


Again, these are just examples, and the way you'll have to edit grub/menu.lst is going to be determined by which operating system you installed, and where.

---

### Post by kingleer on 2008-04-01
> 
Well, it pretty much depends on what the other OS is.
 

I have OS X 86 installed on a Dell Laptop along with Ubuntu 7.10. I'm pretty sure the OS X install uses something called Darwin. 

I found this thread which I think is related: 

> 
[http://forum.insanelymac.com/index.php?showtopic=75978&mode=threaded](http://forum.insanelymac.com/index.php?showtopic=75978&mode=threaded)


---

### Post by angry_johnnie on 2008-04-03
OSX86?  Wow, no idea there!   But, according to the thread you found, you could add something like this to your grub menu:


title Mac OSx86
root (hd1,0)
savedefault
makeactive
chainloader +1


And, just change (hd1,0) to where you actually installed it, and keeping in mind that grub starts counting from zero.

---

