---
title: "Problem with removing Adobe Reader 9."
date: 2012-11-09
forum: General Help
---

### Post by emptycoder on 2012-11-09
I installed Adobe Reader 9 bin file on Ubuntu 12.04, but it was unstable so I had to remove it, the method I used is running a script file inside the main folder named UNINSTALL, the fold is gone but there's an icon remains on GNOME 3 overview,  It says that this application can't be found if I clicked on it.
Did I do something wrong? or is there another method to completely remove it from my system?

Thanks.

---

### Post by ibjsb4 on 2012-11-09
Open a terminal and enter:

gksudo nautilus

Then navigate to your "filesystem" and do a search for adobe and remove the leftover files.
Be sure to remove the right ones, once removed in sudo they are gone forever.

---

### Post by emptycoder on 2012-11-09
Is it really safe to delete all things that related to Adobe? don't forget there's an Adobe Flash Player too?

---

### Post by ibjsb4 on 2012-11-09
Thats why the warning  :)

You could also search just "adobe reader" or "adobe reader 9".  Im just not sure if all related files will appear that way, but would be safer.

---

### Post by emptycoder on 2012-11-09
I searched for Adobe Reader on Filesystem and I found nothing but Icons.
Anything else I can do?

---

### Post by ibjsb4 on 2012-11-09
Take a look in /usr/share/applications

---

### Post by emptycoder on 2012-11-09
It seems the application is no longer exist but for some unknown reasons the icon still appears on Gnome 3 overview. maybe if I could find a way around to remove this icon from overview would do the trick, but I have no idea how to do that. seems to me like a bug.

---

