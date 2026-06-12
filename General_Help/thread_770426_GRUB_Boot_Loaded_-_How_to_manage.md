---
title: "GRUB Boot Loaded - How to manage?"
date: 2008-04-27
forum: General Help
---

### Post by AaronCW on 2008-04-27
Hi! 

I'm trying to find the program to manage Grub Boot Loader! You know, to change the look / feel / text / options / etc ... ??

What I really want to do is just have Ubuntu as the only option with like a 10 second delay so that when/if I want to, I can hit a button an have the option to load XP.

---

### Post by kaboodle_fish on 2008-04-27
Try startupmanager 

I believe it is the repos

---

### Post by akudewan on 2008-04-27
The grub configuration file lies at /boot/grub/menu.lst . This file needs to be edited as root.

If you're not comfortable with it, you can install qgrubeditor, which gives a nice GUI to make the changes you want.
```

sudo apt-get install qgrubeditor

```

Then run the program from Applications > System Tools > QGrubEditor

---

### Post by ghost_ryder35 on 2008-04-27
*** akudewan beet me :) ***
you could just edit
```

sudo gedit /boot/grub/menu.lst

```

---

### Post by elmer_42 on 2008-04-27
Just remember, before you start screwing around with system stuff, to backup the files. In this case you can run this command to back it up in your home folder:
```
sudo cp /boot/grub/menu.lst ~/grub_menu.bak
```
If you find out you messed up GRUB, just run this:
```
sudo cp ~/grub_menu.bak /boot/grub/menu.lst
```

---

### Post by ghost_ryder35 on 2008-04-27
> **elmer_42 said:**
> Just remember, before you start screwing around with system stuff, to backup the files. In this case you can run this command to back it up in your home folder:
```
sudo cp /boot/grub/menu.lst ~/grub_menu.bak
```
If you find out you messed up GRUB, just run this:
```
sudo cp ~/grub_menu.bak /boot/grub/menu.lst
```
come on now, who messes up their system when their tinkering around with things to customize it :---)

---

### Post by AaronCW on 2008-04-27
Thank you everyone for the replies! Man what a helpful community!

I was able to install the QGrubeditor, my first installation via Terminal. Is the Terminal App that comes under Accessories > Terminal the proper one to use when installing and stuff? (I just want to use the big boy one.. :D)

Also, what is this "sudo" command? What else can I do with it? What other programs are available? And how do I know what to type for each program I want? ... I know explaining that could be lengthy, is there a good tutorial on how to use Sudo and a list of Programs? 

Thank you, thank you !!

Aaron

---

