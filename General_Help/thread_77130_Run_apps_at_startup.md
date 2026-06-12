---
title: "Run apps at startup"
date: 2005-10-16
forum: General Help
---

### Post by objorkum on 2005-10-16
I have some commands I want to run before X starts (in the init-scripts). In Slackware, there is a file where you can put commands that will run at the end of the startup. How should I do this in Ubuntu?

---

### Post by taurus on 2005-10-16
I am not in front of my ubuntu box right now but you may want to look in /etc/rc.d for something like rc.local or local.start...

---

### Post by objorkum on 2005-10-16
[QUOTE=taurus]I am not in front of my ubuntu box right now but you may want to look in /etc/rc.d for something like rc.local or local.start...[/QUOTE]

Thanks for your reply. That was what I did in Slackware (/etc/rc.d/rc.local), but the dir rc.d does not exist.

Do I have to create my own init-script? I can do that from the skeleton-file in /etc/init.d.

---

### Post by taurus on 2005-10-16
Yes, you can.  Create it and put whatever you want to start up in there.  Then reboot and see whether the system will read it.  Also, may want to include an echo of some sort so you can see it on the terminal...

echo "Reading /etc/init.rc/rc.local..."

---

### Post by objorkum on 2005-10-16
[QUOTE=taurus]Yes, you can.  Create it and put whatever you want to start up in there.  Then reboot and see whether the system will read it.  Also, may want to include an echo of some sort so you can see it on the terminal...

echo "Reading /etc/init.rc/rc.local..."[/QUOTE]

Yes, I know how to handle init-scripts (rcconf is nice to enable/disable). Would be nice if the Ubuntu developers could enable a file where it was possible to add startup-commands... Except from that, Breezy is awesome.

---

### Post by _26oo_ on 2005-10-16
I think what he wants to point is that if you create that file it will be automatically parsed at startup with no additional setup.

---

### Post by objorkum on 2005-10-16
[QUOTE=_26oo_]I think what he wants to point is that if you create that file it will be automatically parsed at startup with no additional setup.[/QUOTE]

Which file? /etc/rc.d/rc.local? I doubt so. The dir rc.d doesn't even exist, and I used grep to search for rc.local, and no files are reading it.

---

### Post by Dianoga on 2005-12-09
There do seem to be rc*.d directories in /etc/

Not sure why they are there instad of /etc/rc.d/

---

### Post by rlross4455 on 2008-03-05
There is **no** such directory **/etc/rc.d**
There is rc0.d thru rc6.d

---

