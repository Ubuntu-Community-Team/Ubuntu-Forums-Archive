---
title: "E: Could not find package ________"
date: 2008-01-24
forum: General Help
---

### Post by ele_mugv on 2008-01-24
Lookin to install GUI here, I typed: sudo apt-get install (and one of there each time) ubuntu-desktop, gnome, gnome core, xubuntu-desktop, kde, xfce, and al these hav the same error-one in the title of my post..the blank is anyone of the above..pls help

---

### Post by p_quarles on 2008-01-24
Your repository list can get disabled if you install the OS without a working net connection. To check if this is the problem, you can post the results of the following command here:
```
cat /etc/apt/sources.list
```

---

### Post by sekinto on 2008-01-24
What does your sources.list file say?

sudo nano -w /etc/apt/sources.list

---

### Post by ele_mugv on 2008-01-24
> **sekinto said:**
> What does your sources.list file say?

sudo nano -w /etc/apt/sources.list

most of them are restricted

---

### Post by sekinto on 2008-01-24
Are there any sources commented (#) out?

---

### Post by ele_mugv on 2008-01-24
> **sekinto said:**
> Are there any sources commented (#) out?

yeah..lots

---

### Post by taurus on 2008-01-24
You need to remove the # in front of all the lines that start with **deb** & **deb-src**.  Then, save the changes and run

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by p_quarles on 2008-01-24
Just remove the # character on any line that begins with "deb" or "deb-src." Then run this command:
```
sudo apt-get update
```
All should be well once you've done that.

---

### Post by sekinto on 2008-01-24
Well you should uncomment the main, universe, restricted, and multiverse lines (remove the "#").

Then run:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install (package you want to install)

---

### Post by ele_mugv on 2008-01-24
> **sekinto said:**
> Well you should uncomment the main, universe, restricted, and multiverse lines (remove the "#").

Then run:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install (package you want to install)

it says connecting and runs to 44% then it says temporary failure resolving 'website'

---

### Post by taurus on 2008-01-24
Can you just post the darn thing, /etc/apt/sources.list, here then?

```
cat /etc/apt/sources.list
```

---

### Post by sekinto on 2008-01-24
Try a second time, your connection could be glitching. If it still doesn't work you could try this, I don't know if this fix will work though:

sudo aptitude update
sudo aptitude reinstall gnome-gpg gnupg-agent gpgkeys libgpg-error0 libgpg-error-dev python-gnupginterface

---

### Post by ele_mugv on 2008-01-24
> **ele_mugv said:**
> it says connecting and runs to 44% then it says temporary failure resolving 'website'

pls help...

---

### Post by p_quarles on 2008-01-24
> **ele_mugv said:**
> pls help...
Help us help you:
[http://ubuntuforums.org/showpost.php?p=4200143&postcount=11](http://ubuntuforums.org/showpost.php?p=4200143&postcount=11)

---

### Post by ele_mugv on 2008-01-25
> **taurus said:**
> You need to remove the # in front of all the lines that start with **deb** & **deb-src**.  Then, save the changes and run

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

I'm in kernel mode, which kernel should i choose (recovery/normal) and what directory should i be in to execute these commands.

---

### Post by zivxx on 2008-01-25
ive had the same problem before...what i did was
(make sure your'e super user)
nano /etc/apt/sources.list
then delete all the "#" that come before a line that starts with a deb or deb-src besides the one that contains backports or pratner in the line

---

