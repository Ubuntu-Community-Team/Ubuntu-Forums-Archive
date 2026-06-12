---
title: "Install packages onto remote system"
date: 2007-03-29
forum: General Help
---

### Post by ykhun on 2007-03-29
Hi,

I'd a box running 6.10 and its remote. Recently i tried:

sudo apt-get install make

and apt-get ask me to insert the 6.10 CD. I can't since i'm not next to the box. The same thing for aplitude.

Is there a way to install packages w/o inserting the 6.10 installation CD? I'm thinking there must be some ways to install stuff off the universe or some online resources.

Thanks!

---

### Post by ndube on 2007-03-29
> **ykhun said:**
> Hi,

I'd a box running 6.10 and its remote. Recently i tried:

sudo apt-get install make

and apt-get ask me to insert the 6.10 CD. I can't since i'm not next to the box. The same thing for aplitude.

Is there a way to install packages w/o inserting the 6.10 installation CD? I'm thinking there must be some ways to install stuff off the universe or some online resources.

Thanks!

You need to comment out the cd in the /etc/apt/sources.list and uncomment the universe and multiverse repositories.

To comment or uncomment, simply put a # in front of the line. Remember, you need to do this as root.

In the terminal, run the following.

sudo nano /etc/apt/sources.list

make the changes, do a ctrl-o and enter to save, ctrl-x to exit

You can also perform these changes graphically by going to 'System'>'Administration'>'Software Sources'

---

### Post by Clay_Banger on 2007-03-29
> **ndube said:**
> 
You can also perform these changes graphically by going to 'System'>'Administration'>'Software Sources'

or u could just type this at the terminal to edit it graphically:
```
sudo gedit /etc/apt/sources.list
```

---

### Post by Nikron on 2007-03-29
> **Clay_Banger said:**
> or u could just type this at the terminal to edit it graphically:
```
sudo gedit /etc/apt/sources.list
```

He's probably doesn't have a GUI.

---

### Post by ykhun on 2007-03-29
er, yeah... its 6.10 server with no gui.
Anyways, thanks. I'll try the suggestions.

---

