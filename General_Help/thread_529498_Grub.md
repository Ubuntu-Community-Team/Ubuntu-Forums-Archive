---
title: "Grub"
date: 2007-08-19
forum: General Help
---

### Post by lollerpony on 2007-08-19
Hello everyone :D

After using Ubuntu for quite a while, and being unsatisfyed with WINE, Cedegea & Crossover, I decided to make a partition and install windows on it.
So I downloaded GParted live disc, made a 35GB partition for windows and installed windows.

now here is the problem: My PC automatically boots to windows. I installed WINgrub, but don't fully understand how it's supposed to work. what I want is just like the menu which you get when installing ubuntu and windows on the same partition.

can anyone please help?

thanks in advance,

Lollerpony

---

### Post by taurus on 2007-08-19
[https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

---

### Post by confused57 on 2007-08-19
Have you seen this WinGrub guide?:
[http://users.bigpond.net.au/hermanzone/p9.html](http://users.bigpond.net.au/hermanzone/p9.html)

---

### Post by Epilonsama on 2007-08-19
Man, you dont need win grub, all you need is[ Super GRUB disk]("http://supergrub.forjamari.linex.org/") and then restore your Linux Grub, edit your your /boot/grub/menu.lst file by adding:

[I]title		Name of your Windows Version
root		(hdx,y) 
savedefault
makeactive
chainloader	+1[/I]



Where x= number of Hard Drive starting with 0 and y= number of partition starting with 0, you should aslo read the documentation for more info.

---

