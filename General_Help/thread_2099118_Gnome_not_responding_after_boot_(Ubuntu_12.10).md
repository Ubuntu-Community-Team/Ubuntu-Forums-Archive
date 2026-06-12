---
title: "Gnome not responding after boot (Ubuntu 12.10)"
date: 2012-12-28
forum: General Help
---

### Post by cruz12141214 on 2012-12-28
hello, I have been using Ubuntu for about 4 years now, and i ave to say so far I am very happy with it so far.

Recently I have had  serious issue.

here is what happens.....

I boot Ubuntu, log into either Unity, or gnome classic, and if I try to use ANY app it will load up and then gnome just stops working. can't minimize close or maximize, or move the window or any thing,

mouse clicks and some keyboard commands dont work.

the only way i can see to fix it is to (ALT CTRL DEl)  to log out and then log back in

then everything works fine

does any one know whats going on and am I the only one who is dealing with this?

Here is some basic info that I hope will answer any questions yo might have:

Ubuntu version 12.10 x86
Kernal: 3.5.0-21
Gnome: 3.6

I did reinstall (from 64bit to 32 bit), the issue remains even after updates

it happenes even with the generic GPU driver

MY PC specs:

Asus g74sx
CPU:  Intel i7 2630 2.0ghz
RAM: 8gb RAM DDR3
GPU:  Nvidia Geforce GTX 560m 2gb VRAM
HDD 2x 500gb 7200RPM

---

### Post by Calinou on 2012-12-28
Try going into GRUB (hold Shift when booting if needed), then load Ubuntu with rescue mode enabled, then restore GNOME's config to the default one (there should be a setting for that). This saved me once after playing with CompizConfig too much. :)

---

### Post by cruz12141214 on 2012-12-30
Thanks for the option but im not sure thats the problem, because i reinstalled Ubuntu, and I did not mess with ANY settings AT ALL, beyond updating, i just dont get it, this is the first time i rn into this issue, and it does not happen all the time, and the only way i can fix it when it does happen is to log out and log back in using ALT CTRL DEL


but thx for the help

I love linux for my University work as a programmer

which is why i need to fix this annoying issue

---

### Post by cruz12141214 on 2012-12-31
I normally dont like doing this but 
BUMP

---

### Post by fdrake on 2012-12-31
try: ctrl + ALT +T
```

unity --reset
sudo apt-get update

```

---

### Post by cruz12141214 on 2013-01-01
this does not help :(

nothing works when i open apps, all i can do is use the terminal byt ctrl alt T, or log out with ctrl alt Del

I cant use the panel AT ALL, i cant minimize, maximize, close, or move any window with this error, I cant right click the desktop 


I really dont know what to do, I might just use KDE until this problem is resolved,


I really dont know if im explaining the problem correctly

---

### Post by fdrake on 2013-01-01
open the termianl like I told you before
```

less ~/.xsession-errors >~/Desktop/errors

```
attach the file "errors" present on your desktop, to your next post please . Also I'd reinstall again gnome

```

sudo apt-get remove gnome gnome-session*
sudo apt-get install gnome gnome-session*

```
logout and retry.

---

### Post by cruz12141214 on 2013-01-02
well here is the error file; of course again i had to log out to even use firefox and get the command you told me

I will try to reinstall gnome and as a last resort i will use Ubuntu 12.04 and see if the problem is avoidable there

---

### Post by cruz12141214 on 2013-01-02
I jst installed Ubuntu 12.04 to see if the problem existed on that distribution, and it does

mind you this is a fresh install of ubuntu the partition was formated 


but now i get this error with it *see the attached image*


and again the problem disapears if i ctrl alt del to log out, but i have to (tab enter) to press the button since the mouse does not work

---

### Post by cruz12141214 on 2013-01-03
bump

---

### Post by cruz12141214 on 2013-01-03
FOR PETE SAKE


tell me that my issues are not because of my RAT 7 cyborg mouse




AHHHHHHHH

---

### Post by fdrake on 2013-01-03
> **cruz12141214 said:**
> I jst installed Ubuntu 12.04 to see if the problem existed on that distribution, and it does

mind you this is a fresh install of ubuntu the partition was formated 


but now i get this error with it *see the attached image*


and again the problem disapears if i ctrl alt del to log out, but i have to (tab enter) to press the button since the mouse does not work

reagrding your mouse: try to change the sensitivity from the mouse and touchpad program.

---

### Post by fdrake on 2013-01-03
> **cruz12141214 said:**
> well here is the error file; of course again i had to log out to even use firefox and get the command you told me

I will try to reinstall gnome and as a last resort i will use Ubuntu 12.04 and see if the problem is avoidable there

Can you login in inbto gnome-classi . Does the problem persists there too?

---

### Post by cruz12141214 on 2013-01-04
apparently using the rat 7 yes it does, but if i use my other mouse its fine, WTH

meanning as long as i do not have the rat 7 mouse connected Ubuntu seems ok (until i reset X that is by log out log in)

oh well its a minor annoyance that ill deal with until i can fix the rat 7 compatabllity issue, so for now old mouse it is



thx for the help and your patience

---

### Post by fdrake on 2013-01-04
> **cruz12141214 said:**
> apparently using the rat 7 yes it does, but if i use my other mouse its fine, WTH

meanning as long as i do not have the rat 7 mouse connected Ubuntu seems ok (until i reset X that is by log out log in)

oh well its a minor annoyance that ill deal with until i can fix the rat 7 compatabllity issue, so for now old mouse it is



thx for the help and your patience

i am glad you were able to find the solution . please mark the thread as SOLVED so other ppl in the future with your problem will be able to find the solution by reading your posts.

---

### Post by cruz12141214 on 2013-01-04
ill do that as soon as i figure out how



oh wait I found it lol


and just for future reference Ubuntu 12.04 and 12.10 gave me the "cant grab mouse error" because of the RAT mouse series

---

