---
title: "Thunar customized action with sudo doesn't work"
date: 2015-02-08
forum: General Help
---

### Post by fkervin on 2015-02-08
Hi all,

I love thunar's customized actions and I think it's very usefull.

My problem is I'm unable to make any action using sudo. I want to add to the folders a customized action called "Open as administrator", it is, a customized action with "sudo thunar %f", but it does just nothing. If I write "thunar %f" it works but of course it's unusefull at all since the important is opening with sudo.

I mean, system simply ignore or at least apparently ignore the sudo when I would like it to request the admin password and then opening as root. I've read many many how-to's over the internet using this "sudo thunar %f" as example for customized actions but doesn't work for me.

Any help?

Regards and thanks in advance

---

### Post by Morbius1 on 2015-02-08
Maybe thunar is smart enough to know you shouldn't use sudo to open an application with a GUI.
```
gksu thunar %f
```

---

### Post by fkervin on 2015-02-08
Nope :P, I also tried, hehe, thanks everyways :)

I have no problem if the system ask me to enter password, the problem is that does nothing.

If there is another idea....

Regards

---

### Post by Morbius1 on 2015-02-08
Maybe gksu is messed up. Run it in a terminal and see if there are any errors:
```
gksu thunar $HOME
```

---

### Post by fkervin on 2015-02-08
Hi again Morbius1,

Once again you're my hero, hehe

gksu was not installed xD, I were so stupid I didn't try from terminal. After installing it with "sudo apt-get install gksu" it works :D

Many thanks

---

### Post by ajgreeny on 2015-02-08
Install **exo-utils** and **gksudo** and then use the command ```
gksu exo-open %f
``` in the command box of the new custom action to open folders as root; don't forget to select **Directories** in the **Appearance Conditions** tab as well.

I know that works as I use it myself.

---

### Post by fkervin on 2015-02-08
Many thanks ajgreeny,

Now it works, my problem is that i don't really want to make a simply "gksu thunar %f", I'm calling a .hs file using 'gksu path-to-the-sh-file.sh.

It actually works, but when opening the custom action appears the message asking for the administrator password and the message is something like:

```
The application "path-to-the-sh-file.sh" allow to modify important parts of the system
```

I would like that the path to the sh file would not appear here, it seems quite ugly and no professional :P

Any way to change this message? Another solution could be (if possible) making it not to ask for the password but passing it in the custom action. In this way I could control it with a warning window inside the script code.

Regards

---

### Post by kerry_s on 2015-02-08
```
echo "your_password" | sudo -S /path/to/script
```

---

### Post by Holger_Gehrke on 2015-02-08
> **fkervin said:**
> 
I would like that the path to the sh file would not appear here, it seems quite ugly and no professional :P


I just love telling people to RTFM - which in this case actually **is** fine - namely 'man gksu',  and the options '--description' and '--message' especially.

---

### Post by fkervin on 2015-02-09
> **kerry_s said:**
> ```
echo "your_password" | sudo -S /path/to/script
```

Pefect :) Many thanks

> **Holger_Gehrke said:**
> I just love telling people to RTFM - which in this case actually **is** fine - namely 'man gksu',  and the options '--description' and '--message' especially.

Hi Holger_Gehrke,

I have to recognize you're completely right, sorry for not doing it before asking

Regards

---

