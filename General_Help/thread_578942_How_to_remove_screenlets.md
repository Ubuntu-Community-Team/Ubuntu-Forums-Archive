---
title: "How to remove screenlets?"
date: 2007-10-17
forum: General Help
---

### Post by Scooter7 on 2007-10-17
Hi, I downloaded the 0.0.10 screenlets source and compiled and installed, but now I'd like to remove screenlets, as I have no real use for it atm.

I tried ```
sudo apt-get remove screenlets
```, as well as checking in Add/Remove and  Synaptic Package Manager, to no avail.  Is there a way to remove screenlets from my system?

Thanks,

---

### Post by ZOMGxuan on 2007-10-18
I think you have to remove it maually as root through terminal.

The onlly directory i know for it is
/usr/local/share/screenlets

Just delete all screenlet directories using sudo rm in terminal but be careful not to delete anything else

---

### Post by Inxsible on 2007-10-18
The command that you used should remove screenlets from the system. Alternatively you can use the purge command to completely rid your system

```
sudo apt-get remove -purge screenlets
```

---

### Post by Scooter7 on 2007-10-18
Thanks guys, I deleted the folders manually.

Like I said, I originally tried apt-get remove, and I tried Inxsible's suggestion of using the --purge flag, but neither worked.   It just told me that it couldn't find a package called 'screenlets'.   I guess I should use checkinstall in the future. :P

Now, I still have the Screenlets menu entry (Applications -> Screenlets).   Since it's a group, and not a launcher, as far as I know, I can't remove it via System -> Preferences -> Main Menu.   All I managed to do is hide it by unchecking all the Screenlets in the group.

Is there a way to permanently remove it?

Thanks again,

---

### Post by ZOMGxuan on 2007-10-19
You should be able to by right clicking on the screenlets menu in the main menu editor and deleting it.
Like so:
[[IMG]http://img227.imageshack.us/img227/2309/mainmenuss6.th.png[/IMG]](http://img227.imageshack.us/my.php?image=mainmenuss6.png)

---

### Post by Scooter7 on 2007-10-19
Ahh, right, thanks - forgot I could do that, heh. :)

Btw, what theme are you using in that screenshot?   Looks nice.

---

### Post by ZOMGxuan on 2007-10-20
ubuntu studio. The default metacity theme can be gotten from the ubuntu studio repos. If you use emerald you will have to download the ubuntu studio emerald theme and use it as well. A quick search on google should find it.

---

### Post by Scooter7 on 2007-10-20
Aha, okay, thanks.

And thanks again for your help. ;)

---

### Post by nickdr on 2007-10-20
how to i get that screenlets menu? i have screenlets installed but not that menu.

---

### Post by Scooter7 on 2007-10-20
When you compile Screenlets, you can specify if you want a menu package installed as well, I think.

---

