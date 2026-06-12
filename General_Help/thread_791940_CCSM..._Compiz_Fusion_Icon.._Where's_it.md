---
title: "CCSM... Compiz Fusion Icon.. Where's it?"
date: 2008-05-12
forum: General Help
---

### Post by eAi-T0ky0 on 2008-05-12
[i wanna to control in compiz in my ubuntu 8.4 

some effects work like zoom desktop and some alse .. put i wanna to control about it ..

 :( how can i setup Compiz Fusion Icon in my panel?

 :( and how can i active it in startup?

i want find my CompizConfig Settings Manager :(

---

### Post by special ed on 2008-05-12
It should be under Applications-> System Tools

---

### Post by tamoneya on 2008-05-12
first make sure that it is installed:```
sudo apt-get install compizconfig-settings-manager
```
Then launch it by typing:```
ccsm
```

Note: this is all done in terminal (applications->accessories->terminal)

---

### Post by ugm6hr on 2008-05-12
> **eAi-T0ky0 said:**
> i want find my CompizConfig Settings Manager :(

Have you installed it in Synaptic?

Compiz is default, ccsm is not.  It appears as Advanced Desktop Effects in the menu.

---

### Post by lswest on 2008-05-12
also, fusion icon can be installed as well, it's package is called fusion-icon.

---

### Post by eAi-T0ky0 on 2008-05-12
thanks alot .. i get it thanks

but i think my pc get slowly when i active some effects like desktop cube ... maybe my vga card have problem with 3d?? maybe!!! but i feel my pc get slow  when i active cube desktop!! but when i go to my Hardware drivers in adminstion is active and say it is in use with green point and my vga card is nivada :(

i don't know what is problem!! how to know and make sure that my vga card is run well?? and it work good with my effects?? :(

please help!!! :(

---

### Post by tamoneya on 2008-05-12
first of all what is your card? do you have the proprietary driver installed?  Either way if it is sluggish you could install the fusion-icon as mentioned above.  This will let you switch between compiz and metacity.  Metacity doesnt have all the eyecandy and is therefore lighterweight.  This would let you turn on the eye candy only when you wanted to show it off to your friends and such.

---

### Post by eAi-T0ky0 on 2008-05-12
sample when i open the add\remove applations i get my mouse cut :( and the screen become to be black and my pc get so so so slow .... why that??????????? it don't do that with me before ... 

it come to do that when i installed the Compiz Effects Setting and active the desktop cube???


please help :(

---

### Post by eAi-T0ky0 on 2008-05-12
how can i know my the kind of my card?

---

### Post by eAi-T0ky0 on 2008-05-12
the fusion-icon is it not in my panel!!! and I'm new but sorry i don't know how to get the fusion-icon in my panel to control it?? :(:(:(

---

### Post by tamoneya on 2008-05-12
first of all there is no need to panic.  

Here is some info on fusion-icon and how to get it working: [http://tombuntu.com/index.php/2008/03/25/toggle-compiz-with-fusion-icon-in-ubuntu-804/](http://tombuntu.com/index.php/2008/03/25/toggle-compiz-with-fusion-icon-in-ubuntu-804/)

To find out what your graphics card is please type ```
lscpi
``` in terminal and copy the output here and we will tell you what you have and how to improve your compiz framerate.

---

### Post by eAi-T0ky0 on 2008-05-12
root@eai-onlyone:~# lscpi
-su: lscpi: command not found

---

### Post by Eclipse. on 2008-05-12
The command should be lspci.

And you shouldn't really be running as root.Use sudo in front of commands when you need root access.

You will find fusion-icon in system tools, if its not there then you need to install it.You can do this in synaptic package manager or by typing sudo apt-get install fusion-icon in a terminal.

---

### Post by eAi-T0ky0 on 2008-05-12
eai-tokyo@eai-onlyone:~$ su
Password:
root@eai-onlyone:/home/eai-tokyo# lscpi
bash: lscpi: command not found
root@eai-onlyone:/home/eai-tokyo#

---

### Post by Eclipse. on 2008-05-12
> **eAi-T0ky0 said:**
> eai-tokyo@eai-onlyone:~$ su
Password:
root@eai-onlyone:/home/eai-tokyo# lscpi
bash: lscpi: command not found
root@eai-onlyone:/home/eai-tokyo#

Its ls**pci**

And please stop running commands as root.You **dont **need to use root **ever** unless your doing something like installing a program.

---

### Post by tamoneya on 2008-05-12
sorry that was a typo on my part.

---

