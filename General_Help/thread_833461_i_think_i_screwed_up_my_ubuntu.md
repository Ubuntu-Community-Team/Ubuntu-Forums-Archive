---
title: "i think i screwed up my ubuntu"
date: 2008-06-18
forum: General Help
---

### Post by shamguy4 on 2008-06-18
ok i think i screwed up my ubuntu..
I wanted my ati radeon to work so compiz would work..
someone tried helping me and gave me an xorg.conf file and said it would make it work... 
well after restarting i cant seem to get into anything... everything is locked and internet is ot working...
i cant revert back to the backed up xorg.cof file (i have it saved) because i cant save in x11 location i dont have permission

i need help!!

---

### Post by ibuclaw on 2008-06-18
copy it back using sudo

```
sudo cp /path/to/backup/xorg.conf /etc/X11/xorg.conf
```
or if you prefer to do it the visual way,
```
sudo nautilus
```
Regards
Iain

---

### Post by damis648 on 2008-06-18
> **tinivole said:**
> copy it back using sudo

```
sudo cp /path/to/backup/xorg.conf /etc/X11/xorg.conf
```
or if you prefer to do it the visual way,
```
sudo nautilus
```
Regards
Iain

^^ What he said. :popcorn:

---

### Post by TeoBigusGeekus on 2008-06-18
Have you tried through terminal?
```
sudo rm /etc/X11/xorg.conf
sudo mv /place/of/backup/file/nameofbackupfile /etc/X11/xorg.conf
```

---

### Post by shamguy4 on 2008-06-18
thanks ill try...
whats nautilus?

---

### Post by TeoBigusGeekus on 2008-06-18
The equivalent of window$ explorer in Ubuntu.

---

### Post by beckols on 2008-06-18
nautilus is the equivalent of windows explorer. It just gives you a GUI to manipulate files and folders instead of doing it by command line.

---

### Post by shamguy4 on 2008-06-18
nope... now its worse...it says it cant detect my graphics and will run in a lower mode or something...
maybe its from the updates...

---

### Post by shamguy4 on 2008-06-18
its telling me that it can find my graphics card and now I cant even start the stupid thing up!!
I have worked all day on setting up ubuntu but i think my computer just cant handle it...

well thats my linux experience.....yay...
this all started afteri download all the updates thru 
sudo apt-get updates

and does compiz support ati-radeon? or no?
am i wasting my time?

---

