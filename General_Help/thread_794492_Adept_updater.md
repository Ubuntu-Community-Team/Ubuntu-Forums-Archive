---
title: "Adept updater"
date: 2008-05-14
forum: General Help
---

### Post by Scotsgait on 2008-05-14
I used to have  adept-updater appearing in one of the panels to alert me to update but I've now lost it.

Can anyone advise how to get it back, please ?

Many thanks

---

### Post by NightwishFan on 2008-05-14
It me be under the adept configuration somewhere.

Edit: No doesnt look like it. I will look around.

---

### Post by latna on 2008-05-14
It doesn't appear when there aren't any updates to be applied, at least not in hardy. It's still running though.
```
ps -e | grep adept
```
Does adept_notifier show up in the output of that command?

---

### Post by Scotsgait on 2008-05-15
> **latna said:**
> It doesn't appear when there aren't any updates to be applied, at least not in hardy. It's still running though.
```
ps -e | grep adept
```
Does adept_notifier show up in the output of that command?

Running in terminal ? No, nothing appears to have appeared !

---

### Post by Scotsgait on 2008-06-08
I've found the answer [here](http://ubuntuforums.org/archive/index.php/t-196807.html):

[I]Check if there's a file named adept_notifier_auto.desktop in the /usr/share/autostart/ directory. If it isn't there, make one:
1. Open up Kate as root. Press Alt+F2 and enter the following command:
kdesu kate
2. Paste in the following contents:

[Desktop Entry]
Encoding=UTF-8
Exec=adept_notifier
Name=Adept Notifier
Name[da]=Adept underretninger
Name[el]=•¹´¿À¿¯·Ã· µ½·¼µÁÎÃµÉ½ Ä¿Å Adept
Name[es]=Notificador Adept
Name[fr]=Notificateur Adept
Name[it]=Notifica automatica Adept
Name[ka]=Adept èÔÛâçÝÑØÜÔÑÔÚØ
Name[lt]=Adept informuoklis
Name[pt]=Notificador do Adept
Name[sk]=Adept upozornenie
Name[sv]=Adept uppdatering
Name[xx]=xxAdept Notifierxx
X-KDE-autostart-after=panel
Type=Service
X-KDE-autostart-condition=adept_notifierrc:General:Autostart:true
OnlyShowIn=KDE;

3. Save the file as adept_notifier_auto.desktop and save it in the /usr/share/autostart/ directory.[/I]

---

