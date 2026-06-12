---
title: "Ubuntu is fooling me"
date: 2007-03-11
forum: General Help
---

### Post by Elena678 on 2007-03-11
Well, i just installed ubuntu, i used before version 6.06, but during the upgrate, my computer was running stuck. so i made the dicision to do a format, and install the whole thing again :S (6.10 now)

but now, after the install i have some strange things happening with my sceen, green lines, and no mouse cursor, very strange, do somboddy know what i can do aboud that?

Here you can see what i see :P
[img]http://img410.imageshack.us/img410/9098/p1020281id4.jpg[/img]

greetings



ps: sorry for my bad english

[COLOR="Red"]edit: oh yea, i had the same problem with fedora core 6[/COLOR]

---

### Post by chewearn on 2007-03-11
It appears that the video is shifted down in your display area.

Are you using a LCD monitor via VGA?  If yes, there is normally a button (or setup menu item) on the LCD monitor to auto-adjust.

If you are using CRT, could you use the vertical shift adjustment.

---

### Post by Elena678 on 2007-03-11
> **AstalaVista said:**
> It appears that the video is shifted down in your display area.

Are you using a LCD monitor via VGA?  If yes, there is normally a button (or setup menu item) on the LCD monitor to auto-adjust.

If you are using CRT, could you use the vertical shift adjustment.

well, it is a laptop, so i can´t use one of those :(

---

### Post by Elena678 on 2007-03-11
oh wow, this is realy creepy, when i leave my laptop, and it is standing still for some minutes, there is a black screen, when i move the mouse i have a login screen, and when i log in, my screen is normal again, and i have a mouse cursor again (okei, a bit fluffy, but it is back :)

but when i restart, everything is back like it is on the picture abouve.

now it is realy fooling me :P

greetings

---

### Post by der_joachim on 2007-03-11
The screen blanking is a normal thing. Do not worry about that too much. That's just a default setting for your login screen.

What video card  / chipset do you use and which resolution do you have?

---

### Post by Elena678 on 2007-03-11
> **der_joachim said:**
> The screen blanking is a normal thing. Do not worry about that too much. That's just a default setting for your login screen.

What video card  / chipset do you use and which resolution do you have?

don't ask me to much :O i use resolution 1024*768

---

### Post by der_joachim on 2007-03-12
> **Elena678 said:**
> don't ask me to much :O i use resolution 1024*768

Heh. You'll need at least a name for your video card. There's quite an easy way to find out which video card you have though. Open a console and issue the following command: ```
lspci | grep -i vga
```. The lspci command lists your hardware and with grep you can filter all the output.

---

### Post by REDISISTone.nl on 2007-04-06
Hi,

I'm having the same problem with both Feisty and Edgy.
I posted a photo with my result of booting the live cd. 

There is no cursor, all items are not visible until my "inviseble mouse" go over it. :confused: 

My system:

P4 3.0 ghz
1 gig ram 667 mhz
nvidia gforce 6600 GT

Tested with:
Edgy Eft. 6.10
Feisty 7.04

---

### Post by zvacet on 2007-04-06
```
 sudo dpkg-reconfigure xserver-xorg
```

replace **nvidia** with **nv**. After that install Envy script.

---

### Post by REDISISTone.nl on 2007-04-06
> **zvacet said:**
> ```
 sudo dpkg-reconfigure xserver-xorg
```

replace **nvidia** with **nv**. After that install Envy script.

First off all, thank you!!

But could you give me some support, what do you mean with:

> replace **nvidia** with **nv**. After that install Envy script.

Thanx for now

---

### Post by der_joachim on 2007-04-07
> **REDISISTone.nl said:**
> First off all, thank you!!

But could you give me some support, what do you mean with:

Thanx for now

OK. What you need to do is issue the following commands:
```

sudo dpkg-reconfigure xserver-xorg
sudo nano /etc/X11/xorg.conf

```
Find the section "Device" and replace the line ```
 Driver "nvidia"[/code with the line [code]Driver "nv"
```. 

Envy is a script written by one of the regulars of this forum. You can download it from his [site]("http://albertomilone.com/"). Just follow the instructions there and you'll be fine.

---

### Post by Elena678 on 2007-04-24
I have standing there i810, and i stil have the same problem, do i also need to change that, if so, in what do i need to change it, and how do i save it ??

greetings

---

### Post by zvacet on 2007-04-24
If you have same graphic card do as previous posts sed.
```

sudo dpkg-reconfigure xserver-xorg
```

and edit

```
sudo gedit /etc/X11/xorg.conf
```

If you have some other video card I don´t know.Choose** vesa** and when you have working you can go for help for your specific card.

---

### Post by REDISISTone.nl on 2007-04-25
The thing is, I am not able to see what i'm doing when I ```
$ sudo dpkg-reconfigure xserver-xorg
```

I only see the cursor square blinking but nothing else...

Ill try to download the Alternate install CD, and pray that will sort my problems....

---

