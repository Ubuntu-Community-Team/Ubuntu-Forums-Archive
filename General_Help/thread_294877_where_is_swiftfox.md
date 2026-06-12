---
title: "where is swiftfox"
date: 2006-11-07
forum: General Help
---

### Post by TheRingmaster on 2006-11-07
I can't seem to find where swiftfox's folder is on the computer. can some one help. I need to remove the old flash plugin (which I accidentally installed).

---

### Post by taurus on 2006-11-07
Do you have it install, right?

---

### Post by TheRingmaster on 2006-11-07
yes I think so. I installed swiftfox from automatix2 and I installed the flash 7 plugin by mistake. so I want to get rid of the flash 7.

---

### Post by taurus on 2006-11-07
You can use automatix2 to remove flash 7.  Did you try that?

---

### Post by TheRingmaster on 2006-11-07
are you sure that that isn't flash 9? Because my regular firefox says that if is using flash 9

---

### Post by taurus on 2006-11-07
> **TheRingmaster said:**
> are you sure that that isn't flash 9? Because my regular firefox says that if is using flash 9
:confused: 

Did you use automatix2 to install flash 7 as well?

---

### Post by TheRingmaster on 2006-11-07
no, I installed that (through swiftfox and it only is used in swiftfox) by going to a site that used flash. the site asked me to install a plugin. that plugin was the flash 7 plugin

---

### Post by taurus on 2006-11-07
The best way is to remove swiftfox completely and reinstall it again.

---

### Post by TheRingmaster on 2006-11-07
If I do that will the flash plugin be gone?

---

### Post by taurus on 2006-11-07
Should be since it's installed by swiftfox.

---

### Post by strabes on 2006-11-07
the swiftfox directory is /opt/swiftfox when installed with automatix2. You can check this by right clicking on it in your menu, hitting "add launcher to panel" and then right clicking on the new launcher and seeing the command line.

---

### Post by TheRingmaster on 2006-11-07
I searched for swiftfox in synaptic and it is no where to be found.

---

### Post by TheRingmaster on 2006-11-07
I am looking for a sign of flash in /opt/swiftfox and I can't find it. I looked in the folder marked "plugins" and there are two item in there 1)libnullplugin 2)libunixprintplugin

edit: I did find the flash 9 file in /opt/. so I copied and pasted the plugin into swiftfox (in the directory /opt/swiftfox/plugins) and I tested my version here: [http://www.macromedia.com/software/flash/about/](http://www.macromedia.com/software/flash/about/) and i have version 9,0,21,55 installed. so am I cured?

---

### Post by taurus on 2006-11-07
How did you install swiftfox then?  Yes, you can remove those two plugins if you want...

---

### Post by TheRingmaster on 2006-11-07
I installed swiftfox via automatix2


what would those two plugins be?

---

### Post by taurus on 2006-11-07
> **TheRingmaster said:**
> what would those two plugins be

1)libnullplugin 2)libunixprintplugin from Post #13!!!  But since you overwrote them with the new plugins, flash 9, no need to remove anything now...

---

### Post by TheRingmaster on 2006-11-07
no no no. I want to know what they are, not what they are named ( i already know what they are named). 

and no I didn't overwrite anything. I just copied and pasted the new flash 9 file in there.

edit: i don't want to get rid of them if they are important.

---

### Post by TheRingmaster on 2006-11-07
ok so here is what I have done so far. I have taken to the trash all that what was in /opt/swiftfox/plugins and replaced them with a copy of what was in /usr/lib/mozilla firefox/plugins.

why are they locked when they are in the swiftfox plugins folder? here is a pic

---

