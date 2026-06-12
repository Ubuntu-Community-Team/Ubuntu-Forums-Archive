---
title: "[SOLVED] I keep getting this error for every package installation"
date: 2007-06-07
forum: General Help
---

### Post by cc93 on 2007-06-07
Error screenshot:
[img]http://www.uploadyour.info/uploads/images/screenshot-gdebi-gtk59247.png[/img]

EDIT: And I don't have anything opened

---

### Post by gerscht on 2007-06-07
It might be that the update manager is downloading in the background. If that's the case, the update icon in the taskbar should be grey.
Just wait until it's finished, and you'll be able to use synaptic.

---

### Post by cc93 on 2007-06-07
ok but when i try to run update manager  other error apears


[IMG]http://i7.tinypic.com/6fhyyhg.png[/IMG]

---

### Post by cc93 on 2007-06-08
After this i tried fix the problem from terminal but something was wrong  again

[IMG]http://i10.tinypic.com/4pwx9og.png[/IMG]

---

### Post by Kuoi on 2007-06-08
Have you ever installed software before , without errors ?

What programs are running when you want to install , and HOW do you install ?

Using downloaded deb or sources files , or using Synaptic , or do you use the menu "Tools" > "Install/Delete" ?

Kuoi

---

### Post by cc93 on 2007-07-14
there are no programs running 
and i use add or remove programs to install someting
:confused: :confused: :confused: :confused:
btw how can i run 'dpkg - - configure -a'     ?

---

### Post by Nythain on 2007-07-14
sudo dpkg --configure -a
sudo apt clean
sudo apt-get update

dpkg --configure -a will attempt to continue an installation that got interupted (example, terminal got closed, app got closed, liscense wasnt accepted

apt clean will clear apt cache of any debs you were trying to install, you WILL need to tell apt to install any software again that wasnt installed

apt-get update will update apt (im sure you are familiar with this command)

---

### Post by cc93 on 2007-07-14
yes 
thx a lot man :)

---

### Post by cc93 on 2007-07-14
btw   'sudo apt clean'  commant does not exist

---

### Post by cc93 on 2007-07-20
how can i install a .jar package?:confused: 
thx for your time

---

### Post by Spudgun on 2007-07-20
> **cc93 said:**
> btw   'sudo apt clean'  commant does not exist

```
sudo apt-get clean
```

---

### Post by Seisen on 2007-07-20
> **cc93 said:**
> btw   'sudo apt clean'  commant does not exist

Its ```
sudo apt-get autoclean
```

---

### Post by cc93 on 2007-07-24
EDIT: not writing lunguage

---

