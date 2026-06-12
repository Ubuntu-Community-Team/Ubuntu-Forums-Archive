---
title: "Cairo Dock won't autostart"
date: 2017-11-29
forum: General Help
---

### Post by forneus2 on 2017-11-29
I installed **Cairo Dock**, set it up, added **@xcompmgr -n** to manually autostart apps as instructed. But it still doesn't launch at system start. In the settings menu there is an option **Launch on startup** but when I click it nothing happens, there is no check box or confirmation window. What am I missing?

**Lubuntu 16.04** is my distro.

---

### Post by Frogs Hair on 2017-11-29
Are you trying to run the open GL option ?

---

### Post by forneus2 on 2017-11-29
> **Frogs Hair said:**
> Are you trying to run the open GL option ?

Sorry, I'm not that advanced. What is GL option? I just want the dock to launch automatically at system startup.

---

### Post by Frogs Hair on 2017-11-29
There are two options or icons for Cairo Dock and Cairo Dock with open GL . Open GL requires a compositor because it has more effects/eye candy and Lubuntu may not support that option .

These command for startup should still be applicable.

[https://askubuntu.com/questions/91314/how-do-i-add-cairo-dock-with-opengl-to-startup](https://askubuntu.com/questions/91314/how-do-i-add-cairo-dock-with-opengl-to-startup)

---

### Post by forneus2 on 2017-11-29
> **Frogs Hair said:**
> There are two options or icons for Cairo Dock and Cairo Dock with open GL . Open GL requires a compositor because it has more effects/eye candy and Lubuntu may not support that option .

These command for startup should still be applicable.

[https://askubuntu.com/questions/91314/how-do-i-add-cairo-dock-with-opengl-to-startup](https://askubuntu.com/questions/91314/how-do-i-add-cairo-dock-with-opengl-to-startup)

Thanks for your reply. I used [https://www.lifewire.com/make-lubuntu-16-04-look-good-4033938](https://www.lifewire.com/make-lubuntu-16-04-look-good-4033938) as a resource. At the install I did say no to **enable open GL**. Maybe I should have said yes? How can I reconfigure it? My specs are not high - cpu Pentium 1.2Ghz, ram 2Gb, internal graphics. Is it not enough for correct compositing settings?

---

### Post by Frogs Hair on 2017-11-29
According to the instructions you can attempt to use open GL and disable it if there is a problem. Did you perform the other step as well ?  > [COLOR=#101010][FONT=&amp]To make Cairo run at startup right click on the dock and choose cairo dock and then "Launch Cairo Dock On Startup".[/FONT][/COLOR]

---

### Post by forneus2 on 2017-11-29
> **Frogs Hair said:**
> According to the instructions you can attempt to use open GL and disable it if there is a problem. Did you perform the other step as well ?

I did. Right-click on the dock >>cairo configuration >> run on startup. But this menu line is not like checkbox and nothing opens up after clicking on it.

How do I attempt to use openGL? Cannot find the settings option.

---

### Post by Frogs Hair on 2017-11-29
I can't auto start either and the options I used in an earlier version no longer apply . There were once two entries  made to startup applications automatically when autostart was selected and you could enable or disable ether one . I'll try a different command and get back to you.


Edit: The commands posted in the link earlier do work though I am using Ubuntu so things may look different. 
Open GL
 
```
cairo-dock -o

```

Standard


```
cairo-dock -c

```

[http://glx-dock.org/ww_page.php?p=First%20Steps&lang=en](http://glx-dock.org/ww_page.php?p=First%20Steps&lang=en)

---

### Post by tatofuertepr12 on 2018-07-15
i read this on the Net.

I put the Cairo-dock in system startup applications.

Put in the "Command" field: cairo-dock -o
After I pressed ENTER.

Be cool.

and it work, i have Ubuntu 16 OS..

Big thanks to Cibernetico

---

