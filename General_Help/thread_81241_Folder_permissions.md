---
title: "Folder permissions?"
date: 2005-10-24
forum: General Help
---

### Post by JollyRoger on 2005-10-24
Hi, I have a driver that I need to put into the root folder (Is it just called \  ?), but when I just try to drag and drop the program into the folder it says I don't have the right permission to do that.  I tried to right click on the folder to change it, but it says I'm not the owner so I can't change the permissions for that folder, so how do I change this?  I'm a pretty big newbie to Linux, so sorry if this is pretty simple.

thanks

---

### Post by landotter on 2005-10-24
You need to be root to write to that directory. In Ubuntu the easiest thing to do would be to run Nautilus (file manager) as root and do your thing:

to run it as root get a run dialog: alt+f2

type in the box: gksudo nautilus

then enter you password at the prompt.

you're now running a powerful "version" of Nautilus that's capable of much damage so be careful, and do your business.

---

### Post by ikd69 on 2005-10-24
The ever useful ubuntu 5.04 guide at [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) has instructions on how to run nautilus as root (dangerous though it may be).  It basically provides for a handy shortcut to "gksudo nautilus".

You have been warned :smile: 

cheers,
ikd

---

### Post by JollyRoger on 2005-10-24
thanks for the info, I'm not going to screw around too much, so hopefully it'll be ok heh

---

