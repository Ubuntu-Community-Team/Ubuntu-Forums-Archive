---
title: "gnomebaker"
date: 2006-12-10
forum: General Help
---

### Post by aco on 2006-12-10
I have issue with gnomebaker
It dosent want to burn unless i start it from console with sudo
Is there any way to give it permission to function directly from menu, because now it says burning failed no permission

---

### Post by aco on 2006-12-10
Ok second problem.. i installed brasero and wanted to copy cd on the fly....it says after 5secs burning complete

---

### Post by lamego on 2006-12-10
Not sure it resolves your problem but you can get the latest brasero version here:
[http://www.getdeb.net/app.php?name=brasero](http://www.getdeb.net/app.php?name=brasero)

---

### Post by aco on 2006-12-10
No...brasero says burn finished in 5secs...and gnomebaker doesent even want to say anything else but permission denied...my folder is set to read and write permission...help please...could my Samsung SATA dvd recorder be a problem?

---

### Post by wpshooter on 2006-12-10
Go to add/remove programs and install **K3b** and forget about Gnomebaker !!!

---

### Post by schlehmil on 2006-12-10
gnomebaker uses cdrecord to burn files. maybe the suid bit is not set or your user is not in the cdrom group.

> 
$ ls -la /usr/bin/cdrecord
-rwsr-xr-- 1 root cdrom 133 2006-08-17 14:57 /usr/bin/cdrecord


---

### Post by aco on 2006-12-10
$ ls -la /usr/bin/cdrecord-rwxr-xr-x 1 root root 133 2006-08-17 14:57 /usr/bin/cdrecord


I got this back

---

### Post by r4ik on 2006-12-10
I think wpshooters suggestion is NOT bad at all.

---

### Post by aco on 2006-12-10
can k3b function on gnome desktop?

---

### Post by smoker on 2006-12-10
i always start gnomebaker with gksudo and never have a prob.

alt+f2, and type gksudo gnomebaker, it will ask for your password, and away you go.

---

### Post by schlehmil on 2006-12-10
```

$ sudo dpkg-stateoverride --update root cdrom 4754 /usr/bin/cdrecord

```

This will update the file owner and suid bit. Changes are preserved for future cdrecord upgrades.

---

### Post by wpshooter on 2006-12-10
> **aco said:**
> can k3b function on gnome desktop?

Yes, I use it on Ubuntu/gnome almost every day.

---

### Post by Shay Stephens on 2006-12-10
> **wpshooter said:**
> Yes, I use it on Ubuntu/gnome almost every day.
I use k3b on gnome also with success.  I use it over gnomebaker because k3b does data verification and gnomebaker does not.  Will it ever?!?!

---

### Post by brucewagner on 2008-01-22
**Stupid Question of the Day:**

If KDE applications run just as well on GNOME...   

What the heck is the difference?   

Is there any reason at all to avoid using KDE applications?   

Is there any reason at all to have a "preference" for GNOME applications over KDE applications on Ubuntu?

---

### Post by notwen on 2008-01-22
> **brucewagner said:**
> **Stupid Question of the Day:**

If KDE applications run just as well on GNOME...   

What the heck is the difference?   

Is there any reason at all to avoid using KDE applications?   

Is there any reason at all to have a "preference" for GNOME applications over KDE applications on Ubuntu?

GNOME apps use the [GTK+]("http://en.wikipedia.org/wiki/GTK%2B") toolkit, while KDE apps use the [QT]("http://en.wikipedia.org/wiki/Qt_%28toolkit%29") toolkit.  Both KDE and GNOME apps will work in either DE, but will require additional packages to work in the other.  I myself personally run GNOME and prefer it over KDE, but also use a couple of KDE apps.  Some people like to stress that they have all of these un-needed KDE packages installed in their GNOME desktop, but it's more than likely that they have installed a KDE app that requires the additional KDE packages.  Hope this helps.

---

### Post by brucewagner on 2008-01-22
So KDE applications will run FLAWLESSLY under GNOME....  Yes?

They are not going to have any features, or functionality, that could end up "broken", or non-functioning, because I'm running them under GNOME (instead of KDE)....?

---

### Post by Shay Stephens on 2008-01-23
> **brucewagner said:**
> So KDE applications will run FLAWLESSLY under GNOME....  Yes?

They are not going to have any features, or functionality, that could end up "broken", or non-functioning, because I'm running them under GNOME (instead of KDE)....?

I have never had a problem running kde apps in gnome.  I don't give it a second thought now.  It's nice having the flexibility :-)

---

### Post by stchman on 2008-01-23
> **brucewagner said:**
> So KDE applications will run FLAWLESSLY under GNOME....  Yes?

They are not going to have any features, or functionality, that could end up "broken", or non-functioning, because I'm running them under GNOME (instead of KDE)....?

Only thing about running KDE apps under Gnome is that you need to load kdeinit at startup for faster loading of KDE apps.

---

### Post by Pygi on 2008-01-23
> **Shay Stephens said:**
> I use k3b on gnome also with success.  I use it over gnomebaker because k3b does data verification and gnomebaker does not.  Will it ever?!?!

You're more then welcome to submit me a patch, and it's working I'll be more then glad to commit it.

KR,
M.

---

### Post by Shay Stephens on 2008-01-23
> **stchman said:**
> Only thing about running KDE apps under Gnome is that you need to load kdeinit at startup for faster loading of KDE apps.

Well, you may want to, but you don't have to.  I don't, I just wait for the app to launch.  No problems, and the wait is not that long on my machines.

---

### Post by Shay Stephens on 2008-01-23
> **Pygi said:**
> You're more then welcome to submit me a patch, and it's working I'll be more then glad to commit it.

KR,
M.

Sorry, I am not a programmer at this point in time.  The only patches I do right now are on my bicycle tires ;-)

---

