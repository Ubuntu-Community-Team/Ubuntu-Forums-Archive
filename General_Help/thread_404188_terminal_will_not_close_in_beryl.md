---
title: "terminal will not close in beryl"
date: 2007-04-08
forum: General Help
---

### Post by Donhu on 2007-04-08
after running beryl, i try to close the terminal and my system freezes, but it will work perfectly fine if i leave it open. it is also displaying an error message :

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

libGL warning: 3D driver claims to not support visual 0x5b
Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

libGL warning: 3D driver claims to not support visual 0x5b
Reloading options

---

### Post by NikoC on 2007-04-08
Do you open the terminal to startup beryl? If so try alt+f2 and type the command you normally use in terminal to execute beryl (I'm guessing 'beryl' or 'beryl-manager').

---

### Post by Donhu on 2007-04-08
thanx alot man...that did work, u seem to kno wat ure doin, tell me also, i had like 13 desktops after i start beryl tho, how do i reduce them to four? i cannot do it in the regular option in desktop settings
thanks in advance

---

### Post by NikoC on 2007-04-09
Hmm I'm not really a Beryl expert, but perhaps this is a solution for the numerous desktops:
Beryl Settings Manager > General Options > Main tab 
Scroll down and there is an option 'Number of Desktops'... in my case I 've set it to '1'.

If this doesn't help try the beryl forums or post a new thread on ubuntu, there are some serious Beryl experts out there!

---

