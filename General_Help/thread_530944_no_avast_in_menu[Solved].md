---
title: "no avast in menu[Solved]"
date: 2007-08-21
forum: General Help
---

### Post by girard on 2007-08-21
i had been successful in previous installations of avast with fiesty. but for some weird reason, my installation now, after doing a clean install, has some quircks i can't figure out. avast is installed and it run, updates, and everything, but i somehow lost it's icon and menu entry in the accessories menu. i understand that i can create a custom launcher for this, but i was just wondering what's wrong. could it be a mishap in the fiesty upgrade (i used online upgrade from edgy)? o something else... any ideas on this?

also when i run avast from the terminal, i get this:

> 
(process:6644): Gdk-WARNING **: locale not supported by Xlib

(process:6644): Gdk-WARNING **: can not set locale modifiers


i know there could be workarounds, but what i want to find out is why the installation isn't working like it used to. i've completely removed it from synaptics, reinstalled, installed via dpkg, but the entry still doesn't show up in the menu...

---

### Post by girard on 2007-08-21
found the answer...

[http://www.ubuntugeek.com/avast-antivirus-for-ubuntu-desktop.html](http://www.ubuntugeek.com/avast-antivirus-for-ubuntu-desktop.html)

i hope this could be of use to someone else, because i think that entry should have been added automatically during the installation.

now i can't recall doing that during my previous installations, but i might have probably... lol

---

### Post by AceofSpades19 on 2007-08-21
you need avast why?

---

### Post by girard on 2007-09-04
> **AceofSpades19 said:**
> you need avast why?

because my notebook still runs XP, and i use it to cure my sister's flash disk of viruses! really.

---

### Post by bkrispy on 2007-09-18
This worked perfectly!  Thanks a lot!  Nice and simple instructions for a beginner Ubuntu user!

---

### Post by Gremlinzzz on 2007-09-18
> **girard said:**
> found the answer...

[http://www.ubuntugeek.com/avast-antivirus-for-ubuntu-desktop.html](http://www.ubuntugeek.com/avast-antivirus-for-ubuntu-desktop.html)

i hope this could be of use to someone else, because i think that entry should have been added automatically during the installation.

now i can't recall doing that during my previous installations, but i might have probably... lol

heres the competition
[http://www.howtoforge.com/avg_antivirus_ubuntu_feisty](http://www.howtoforge.com/avg_antivirus_ubuntu_feisty)

---

### Post by wormser on 2007-10-14
> **girard said:**
> found the answer...

[http://www.ubuntugeek.com/avast-antivirus-for-ubuntu-desktop.html](http://www.ubuntugeek.com/avast-antivirus-for-ubuntu-desktop.html)

i hope this could be of use to someone else, because i think that entry should have been added automatically during the installation.

now i can't recall doing that during my previous installations, but i might have probably... lol

It worked for me.  Thanks for posting the solution.

> you need to run a script from the following location

cd /usr/lib/avast4workstation/share/avast/desktop

sudo ./install-desktop-entries.sh install

This will complete the application menu setup.

---

### Post by girard on 2007-11-02
> **Gremlinzzz said:**
> heres the competition
[http://www.howtoforge.com/avg_antivirus_ubuntu_feisty](http://www.howtoforge.com/avg_antivirus_ubuntu_feisty)

ah yes...  but i've tried it and avast seems to run better on linux. although i do have avg, eversince, on my xp system. if i recall correctly, i had problems with permissions with avg on linux. plus, avast looks, feels and functions better. they're both good anyway, so whichever works for you...  :)

---

