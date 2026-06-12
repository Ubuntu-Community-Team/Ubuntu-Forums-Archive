---
title: "How to open Gparted"
date: 2015-12-27
forum: General Help
---

### Post by sotires on 2015-12-27
Hello, 
I installed Gparted via the Ubuntu software centre on a recently installed Ubuntu 15.10
The installation wenth through with no problem. 
But now I can't find it. I have used Gparted in the past with previous versions of Ubuntu. 
Has the procedure changed? Or is my memory failing?
Anyway, how do you open it?
Thanks

---

### Post by bashiergui on 2015-12-27
Type "gparted" in the search lens. 
Or type in a terminal ```
sudo gparted
```

---

### Post by sudodus on 2015-12-27
In standard Ubuntu with Unity: Use Dash - Click on the Ubuntu symbol in the top left corner. Type gp, and you will get the gparted icon to click ...

---

### Post by yetimon_64 on 2015-12-27
> **bashiergui said:**
> ...
Or type in a terminal ```
sudo gparted
```

@ OP, if using sudo with a graphical application I would suggest changing that command to ... 
```
sudo -H gparted
```

Doing so will correctly set the home environment to that of root, which will protect your user profile from accidental permissions/ownership changes. From "man sudo"...
> -H, --set-home
                 Request that the security policy set the HOME environment variable to the home directory spec&#8208;
                 ified by the target user's password database entry.  Depending on the policy, this may be the
                 default behavior.

See also, [https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo), this says to use "gksudo" or "gksu". If I recall correctly I have had to add "gksu" to recent ubuntu installs, it is not in the standard install nowadays. However using the "-H" switch with "sudo" should adequately protect your install. Note some graphical applications are ok to use with sudo, some aren't and will at times cause damage. As a general guide either "gksudo" or using the "-H" switch with "sudo" should protect you a bit more. 
Cheers, yeti.

---

### Post by sudodus on 2015-12-28
+1 for ```
sudo -H gui-program
```

Thanks for the heads up  *yetimon_64*

---

### Post by v3.xx on 2015-12-28
> **sudodus said:**
> +1 for ```
sudo -H gui-program
```

Thanks for the heads up  *yetimon_64*
 yes +1

---

### Post by sammiev on 2015-12-28
I had the same happen to me with 15.10, so I must add myself to this thread.

I had the icon and the only thing that worked for me in terminal was "parted".

A fresh install fix the problem which I was hoping to find a fix without do so.

---

### Post by sudodus on 2015-12-28
Please explain sammiev! Was gparted installed, but did not work?

Was there any response at all, when you tried

```
sudo -H gparted
```

or was it not available via a menu or dash?

---

### Post by deadflowr on 2015-12-28
I think you run gparted with pkexec for superuser authentication.
```
pkexec gparted
```

---

### Post by sammiev on 2015-12-28
> **sudodus said:**
> Please explain sammiev! Was gparted installed, but did not work?

Was there any response at all, when you tried

```
sudo -H gparted
```

or was it not available via a menu or dash?

There was no response or error codes returned in terminal.

I was using gparted with no issues on a fresh install but stopped working shortly after. ( 2 or 3 days later )

Still was able to use parted with no issues. ( Strange )

---

### Post by sammiev on 2015-12-28
> **deadflowr said:**
> I think you run gparted with pkexec for superuser authentication.
```
pkexec gparted
```

Wish I would have thought of that. :(

---

### Post by deadflowr on 2015-12-28
> **sammiev said:**
> Wish I would have thought of that. :(
Me laughs because I forgot to add can, as in
"I think you **can** run gparted with pkexec for superuser authentication."
Somewhere between my brain and my fingers that wondered off to the can...

---

### Post by sudodus on 2015-12-28
> **sammiev said:**
> There was no response or error codes returned in terminal.

I was using gparted with no issues on a fresh install but stopped working shortly after. ( 2 or 3 days later )

Still was able to use parted with no issues. ( Strange )

It is hard to know what was causing the problem. ***gparted*** has been very stable for me in all versions of Ubuntu since gutsy gibbon. It could have been 'any' of the libraries involved, maybe something related to the GUI.

---

