---
title: "Emerald Theme Manager"
date: 2008-07-07
forum: General Help
---

### Post by Wherethebeef7 on 2008-07-07
Hello, I am a new user to Linux: Ubuntu, and I was wondering how to properly install the theme Kore ([http://www.gnome-look.org/content/show.php/Kore+Suite?content=54701](http://www.gnome-look.org/content/show.php/Kore+Suite?content=54701)) with Gnome. 

Reading the installation instructions gave me this.

> 1.) Extract the Package and just hit on Install in "Emerald Theme Manager". Select all the themes (3) and finished.

2.) To set up the config, open up Beryl-Settings and hit Import at the "General/profiles" tab. Select the included config file. VOILA!

Now I've extracted the package into the Emerald Theme Manager, but I don't actually know how to select the theme. 

Would like tips and advice, thanks. :)

---

### Post by ravenvii on 2008-07-07
That's a KDE theme, not a GNOME theme.

The tag of the thread implies you're using Ubuntu? Or are you actually using Kubuntu?

---

### Post by Wherethebeef7 on 2008-07-07
I am using Ubuntu. What is KDE?

---

### Post by sayakb on 2008-07-07
First of all, welcome to Ubuntu and the forums! :D
Does the package have a **.emerald** file in it? Then open emerald theme manager, press **Install** and select the .emerald file. The file should appear in the emerald theme manager's list. To start emerald, press Alt+F2 and enter **emerald --replace** and press enter. To start emerald at startup, goto *System->Preferences->Sessions*, Press **Add**, enter name as **Emerald **and command as **emerald --replace** and done!

---

### Post by Wherethebeef7 on 2008-07-07
Neat, thanks a bunch! :)

---

### Post by sayakb on 2008-07-07
Np.. glad I could help. Please mark the thread as solved (Thread tools->Mark thread as solved)

---

### Post by zmdmw52 on 2009-09-20
> **sayakb said:**
> First of all, welcome to Ubuntu and the forums! :D
Does the package have a **.emerald** file in it? Then open emerald theme manager, press **Install** and select the .emerald file. The file should appear in the emerald theme manager's list. To start emerald, press Alt+F2 and enter **emerald --replace** and press enter. To start emerald at startup, goto *System->Preferences->Sessions*, Press **Add**, enter name as **Emerald **and command as **emerald --replace** and done!
[FONT=Fixedsys]Does this replace Metacity as the Window Manager with Emerald ? 
[I]
Do not mean to cross-post, but the Windows titlebar height is too big and I cannot find a setting anywhere to decrease it. Emerald has this setting, but I don't know what it is (Window Manager/Theme Manager ?) and how to use it.[/I][/FONT]

---

### Post by zero.crash.overwrite on 2010-11-09
hello there... i am very new to the Ubuntu linux OS. i was using windows XP... very boring when virus hits the hard disk....
 
I was wondering where can i download the emerald theme manager since i cannot connect directly to the internet from Ubuntu (i.e I am using broadbrand, so i have to download it from windows and install in Ubuntu).

---

### Post by zero.crash.overwrite on 2010-11-09
by the way i am using ubuntu 10.10

---

### Post by ave2 on 2010-11-23
I had the same problem- there may be an easier way but this is what I did
go to system> admin> synaptic package manager
type in emerald. 
click mark for installation
click on file>generate package download script
save it to a file. 
that file will contain all the .deb files that need to be downloaded
copy that file to your windows pc
**here there must be an easier way***
I opened the file in wordpad- for emerald there were the addresses of 2 files that needed to be downloaded.
download those 2 files manually
copy those 2 .deb files plus the script into the same directory in ubuntu
go back to synaptic- close and open again so that nothing is marked for installation
click on file>add downloaded packages
point to the directory where script and .deb files are stored

if there is an easier way I would love to know about it

---

### Post by Cloud4Twenty on 2011-01-27
Thanks sayakb for the resolution. I got it all installed and everything on my own, but I was kinda scratching my head on how to get the theme to run. After reading your post I got it all goin. :D

---

