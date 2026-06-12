---
title: "How to personalize the login screen?"
date: 2006-07-01
forum: General Help
---

### Post by dolarsrg on 2006-07-01
Hi everyone!

Sorry for doing such an stupid question, but I've been looking everywhere and I've not found any way. How can I personalize the login screen (the one where you have to write the login and password) in Kubuntu?

Thanks a lot!

---

### Post by sYs^ on 2006-07-01
Check these pages:

[http://www.kde-apps.org/content/show.php?content=22120](http://www.kde-apps.org/content/show.php?content=22120)
[http://www.kde-look.org/index.php?xcontentmode=40](http://www.kde-look.org/index.php?xcontentmode=40)

---

### Post by DarkOx on 2006-07-01
Fire up Adept, and search for "kcontrol-kdmtheme". You need to install that package. Then, open up a terminal, and type "kcontrol". From the program that loads, go to "System Administration" then "KDM Theme Manager". Download any of the themes from [http://www.kde-look.org/index.php?xcontentmode=40](http://www.kde-look.org/index.php?xcontentmode=40). From the theme manager, just click "Install New Theme", select the file you downloaded, and it will be automatically installed for you. Just select it from the list, apply it, and you've got yourself a shiny new login theme.

---

### Post by aysiu on 2006-07-01
You'll need to [enable extra repositories](http://www.psychocats.net/ubuntu/sources) before you can install *kcontrol-kdmtheme*

You'll also have to launch KControl as root in order for the option to appear: ```
kdesu kcontrol
```

---

### Post by Jucato on 2006-07-01
First, you need to have kdmtheme installed. This is the KDM Theme Manager, which allows you to install other KDM themes. AFAIK, you don't need to have kcontrol-kdmtheme installed (kdmtheme will add itself to KControl/System Settings)

Next, look for a nice KDM theme from [http://www.kde-look.org](http://www.kde-look.org) . Download it somewhere on your /home directory (it will come as a .tar.gz archive).

Open up System Settings/KControl and go the KDM Theme Manager (under the Administration Group). Enter Administrator Mode and enter your password. Click on Install New Theme and locate the theme you just downloaded. Click OK and  then click Apply. That should get you going.

---

### Post by v4169sgr on 2006-07-01
Anyone know where to get a nice KDM faces theme like the human-list one for GDM? I am currently using GDM to log in to KDE because of this ...

Many thanks!

---

### Post by sYs^ on 2006-07-03
Just check the 2nd post ...

---

### Post by v4169sgr on 2006-07-03
[QUOTE=sYs^]Just check the 2nd post ...[/QUOTE]
Maybe I'm missing something, but I've spent a long time trawling through kde-looks and not found ANY KDM faces themes ... :cry:

---

### Post by aysiu on 2006-07-03
[QUOTE=v4169sgr]Maybe I'm missing something, but I've spent a long time trawling through kde-looks and not found ANY KDM faces themes ... :cry:[/QUOTE]
This may help.

---

### Post by v4169sgr on 2006-07-09
> **aysiu said:**
> This may help.
Sorry if I am missing anything here, but none of those are faces themes ... by faces themes I mean like human-list for GDM.

---

### Post by aysiu on 2006-07-09
> **v4169sgr said:**
> Sorry if I am missing anything here, but none of those are faces themes ... by faces themes I mean like human-list for GDM.
I don't know what you mean, actually.

---

### Post by Jucato on 2006-07-09
I think what he meant was that in the GDM Login options, one of the themes there is called "Faces". He's right. AFAIK, there's no version of that theme in KDE. 

A possible workaround is to use a very minimal KDM Login theme, then manually change the background to use the Faces theme background.

---

### Post by v4169sgr on 2006-07-10
Go look at the GDM "HumanList" faces theme. What happens here is that a small picture can be selected for each user and displayed on the login screen. Clicking on the picture + login name prepopulates the 'username' field leaving just the 'password' field to be completed.

I had this for years and years with SuSe as default ...

---

