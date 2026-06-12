---
title: "Help"
date: 2007-08-15
forum: General Help
---

### Post by Asho on 2007-08-15
I know this probally sounds really stupid :confused: but I have Ubuntu Server. How do I get onto the desktop? So it isn't all writing.

---

### Post by Steveway on 2007-08-15
A Server has no GUI, it's not useful and adds security risks.
But if you want to install one despite that then type:
sudo apt-get install ubuntu-desktop
it should install Gnome.
And you should be able to start X with the command:
startx
afterwards.

---

### Post by Asho on 2007-08-15
Ok Thanks. From the desktop can you install stuff ect? and can you revert back to not-GUI?

---

### Post by Asho on 2007-08-15
Also what do you mean startx? do I type that or replace x with somethings?:confused:

---

### Post by Steveway on 2007-08-15
Yes, with Add/Remove, Synaptic or using a command like I gave you.
Yes, either remove gnome using Synaptic or the command-line or type in this command while Gnome is running:
/etc/init.d/gdm stop
EDIT: The command startx starts the graphical X-server called Xorg.

---

### Post by mudpuddlestones on 2007-08-15
yes, once on the desktop go to
Applications>Add/Remove> whatever you want

---

### Post by Asho on 2007-08-15
Keeps on saying Cannot Find package ubuntu-desktop

---

### Post by Steveway on 2007-08-15
You need a working connection to the internet.
What does the command ifconfig spit out?

---

### Post by Asho on 2007-08-15
Oh I don't have internet on that comp. Any other way?

---

### Post by Steveway on 2007-08-15
You could download the Desktop-version of Ubuntu and burn it to a CD.
Then you could install that or you could insert it and try the command again, Ubuntu will then fetch the files from the CD.
But it would be better to have internet on the computer you are installing Ubuntu on, because you'll miss a lot of things if you don't have, and it is a server, isn't it meant to be on the internet.

---

### Post by Asho on 2007-08-15
Lol Well I how do you change directory to cd?

---

### Post by Steveway on 2007-08-15
It should do this automatically.
If it does not you can use the apt-cdrom command:
sudo apt-cdrom add

---

### Post by Asho on 2007-08-15
Now I am install apache so a cd /cdrom/ because I have the gzipped package on there and it says No such file when I try and un-gzip it :(.

Would this be better on the desktop?


Please note: I burned on Windows system. Does this matter?

---

### Post by Asho on 2007-08-15
Also where do I download the GUI?

---

### Post by Steveway on 2007-08-15
I gave you all necesarry informations.
Reread if you didn't understand it.

---

### Post by Asho on 2007-08-15
> **Steveway said:**
> I gave you all necesarry informations.
Reread if you didn't understand it.
I did that but it says ...Not Debian disk

---

### Post by Asho on 2007-08-15
Where do I download?

---

### Post by Asho on 2007-08-15
Does it matter if I burn CDs with Windows then use them on Linux?

---

### Post by gecko94 on 2007-08-15
no, and the gui is included with the desktop cd/dvd, which is found [[COLOR="Red"]here[/COLOR]]("http://www.ubuntu.com/getubuntu/download")

---

