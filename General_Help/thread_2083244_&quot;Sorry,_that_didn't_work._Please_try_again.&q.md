---
title: "&quot;Sorry, that didn't work. Please try again.&quot; error message when trying to sudo."
date: 2012-11-11
forum: General Help
---

### Post by miatawnt2b on 2012-11-11
I just upgraded from 12.04 to 12.10.  Now, I have a problem when launching synaptic.  I get the sudo authentication dialog, but after a second, an error appears at teh bottom of the window that says "Sorry, that didn't work. Please try again."

Sudo from a terminal works properly as does gksudo. It's just the gnome3 sudo apparently that does this.

Any ideas?
-J

---

### Post by vasa1 on 2012-11-12
> **miatawnt2b said:**
> ... It's just the **gnome3 sudo** apparently that does this.
...

What do you mean by "gnome 3 sudo"? That may give people a clue. AFAIK, Synaptic is still a gtk2 app.

---

### Post by mc4man on 2012-11-12
By default synaptic uses polkit, does this happen if you start synaptic with 
```
pkexec synaptic
```

---

### Post by miatawnt2b on 2012-11-12
> **mc4man said:**
> By default synaptic uses polkit, does this happen if you start synaptic with 
```
pkexec synaptic
```

THat's interesting.  It does not happen when I run pkexec from a terminal.
-J

---

### Post by philinux on 2012-11-12
> **miatawnt2b said:**
> THat's interesting.  It does not happen when I run pkexec from a terminal.
-J

What does this reveal.

```
cat /usr/share/applications/synaptic.desktop
```

---

### Post by miatawnt2b on 2012-11-12
> **philinux said:**
> What does this reveal.

```
cat /usr/share/applications/synaptic.desktop
```

```


m@Chronos:~$ cat /usr/share/applications/synaptic.desktop
[Desktop Entry]
Name=Synaptic Package Manager
GenericName=Package Manager
Comment=Install, remove and upgrade software packages
Exec=synaptic-pkexec
Icon=synaptic
Terminal=false
Type=Application
Categories=PackageManager;GTK;System;Settings;
NotShowIn=KDE;
X-Ubuntu-Gettext-Domain=synaptic

```

---

### Post by mc4man on 2012-11-12
> Now, I have a problem when launching synaptic 
If you were to clarify _How_ you are launching synaptic then should be easy to fix
(& what session you use  - unity, gnome-shell, classic

You can, if desired, remove the need to auth synaptic   thru a .pkla
(only allows users in the sudo (previously known as admin) group, so safe in a multi-user setup

---

### Post by miatawnt2b on 2012-11-12
> **mc4man said:**
> If you were to clarify _How_ you are launching synaptic then should be easy to fix
(& what session you use  - unity, gnome-shell, classic

You can, if desired, remove the need to auth synaptic   thru a .pkla
(only allows users in the sudo (previously known as admin) group, so safe in a multi-user setup


I am launching from gnome-shell. I type synaptic into the search bar and hit enter.

Tried both via terminal... launching via 'synaptic-pkexec' causes the error, but 'pkexec synaptic' does not

```
w@Chronos:~$ more /usr/bin/synaptic-pkexec
#!/bin/sh
pkexec "/usr/sbin/synaptic" "$@"

```

-J

---

### Post by mc4man on 2012-11-13
Well - 
In gnome-shell you can't run synaptic-pkexec script directly from a terminal or probably the  run command box - it will produce the "Sorry, that didn't work. Please try again." error 

You should though have no issue running from the .desktop, to check that run this command, either from a terminal or Alt+f2
```
gtk-launch synaptic
```
 
If that works then in gnome-shell go to the hot corner,search synaptic & d. click on the icon, - does that work?

---

### Post by miatawnt2b on 2012-11-13
> **mc4man said:**
> 
You should though have no issue running from the .desktop, to check that run this command, either from a terminal or Alt+f2
```
gtk-launch synaptic
```
 
If that works then in gnome-shell go to the hot corner,search synaptic & d. click on the icon, - does that work?

'gtk-launch synaptic' in a terminal works

hot corner search for synaptic, click icon, gives the error.

---

### Post by mc4man on 2012-11-13
Bit of a mystery. 
1st maybe check there are no other synaptic.desktop's around
```
ls ~/.local/share/applications/

ls /usr/local/share/applications/

```
If not then could you browse to /usr/share/applications & d. left click on the 1st synaptic icon as in screen (the 2nd one is synaptic-kde.desktop

You could also try this - 

In system settings set up a new user (admin), log in to & try. If it works then it's one of your local config files, some trial & error will find out which one
(you can remove the new user later

(Or we could just remove the need to auth synaptic which i do here but better to resolve this anyway..

---

### Post by miatawnt2b on 2012-11-13
> **mc4man said:**
> Bit of a mystery. 
1st maybe check there are no other synaptic.desktop's around
```
ls ~/.local/share/applications/

ls /usr/local/share/applications/

```
If not then could you browse to /usr/share/applications & d. left click on the 1st synaptic icon as in screen (the 2nd one is synaptic-kde.desktop

You could also try this - 

In system settings set up a new user (admin), log in to & try. If it works then it's one of your local config files, some trial & error will find out which one
(you can remove the new user later

(Or we could just remove the need to auth synaptic which i do here but better to resolve this anyway..

BINGO!  Thanks!
There was a synaptic.desktop in ~/.local/share/applications
I deleted it and it works normally now.
-J

---

