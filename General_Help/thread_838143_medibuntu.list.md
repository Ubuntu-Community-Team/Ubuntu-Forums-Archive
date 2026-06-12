---
title: "medibuntu.list"
date: 2008-06-23
forum: General Help
---

### Post by PureBreed on 2008-06-23
Hi

Im struggling to use my synaptics update manager, I keep on getting the error:   

'E:Type '--13:40:35--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'

Please help!

---

### Post by Kevbert on 2008-06-23
Hi.  Looks like you've got a file corruption in that file.
In terminal, enter
```
sudo gedit /etc/apt/sources.list.d/medibuntu.list
```
and remove the time.
Here's a copy of my file:
```
## Medibuntu - Ubuntu 7.10 "gutsy gibbon"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ gutsy free non-free
# deb-src http://packages.medibuntu.org/ gutsy free non-free
```
Edit and save the file then try updating with
```
sudo apt-get update
```

---

### Post by vincentvee on 2008-06-23
> **PureBreed said:**
> Hi

Im struggling to use my synaptics update manager, I keep on getting the error:   

'E:Type '--13:40:35--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'

Please help!
open the terminal and type 
```
sudo nautilus
```then navigate to /etc/apt find the file that sources.list
open it (as root) it should open in root if you launched sudo nautilus
add this to the bottom of it:
```
 deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free
```that is the medibuntu repository, there might be other work but i don't recall, but you might have to delete the medibuntu generated repo, i'm not sure so as k around before you do fu(king with it too much, like i said it has been a long time since i had this problem, but the problem is definately with the medibuntu generated list which i think is in sources.list.d
anyway, even if you have to reinstall the whole thing, remember medibuntu repo's are better added like i described above not in the manner the medibuntu site, even though i know those guys know what they are doing, it always worked better for me like that
like i said tho, ask around a bit before you fu(k with it

---

