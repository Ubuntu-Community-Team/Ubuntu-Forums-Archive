---
title: "unable to remove fonts"
date: 2015-06-13
forum: General Help
---

### Post by Alduins_Khajiit on 2015-06-13
Now i want to remove some of them But i am unable to find Option To remove the fonts .. 
I have visited on  
/usr/shared/fonts 
But the fonts are not there.. :sad:
they are also NOT in ~/.fonts as told to look [here]("http://ubuntuforums.org/showthread.php?t=1905174") it would NOT let me post there to say it didn't work
the ~/.fonts have "0 items" and the /usr/shared/fonts only has the ones installed by the OS
I have searched whole computer But unable to find where they are installed

---

### Post by Dennis N on 2015-06-13
Also look in the folder **~/.local/share/fonts**

---

### Post by Dennis N on 2015-06-13
I suggest you try font manager to manage your fonts. It will scan for and catalog all fonts, and will give you their filenames and locations. Fonts can also be installed, deactivated or removed (see the Help button for information on these features.)

---

### Post by ian-weisser on 2015-06-14
> **Alduins_Khajiit said:**
> Now i want to remove some of them But i am unable to find Option To remove the fonts .. 

Lots of possible places fonts could be.
Several possible ways they could be installed.
Uninstalling fonts properly depends upon knowing how and where the fonts were installed. Sometimes it's as simple as locating and deleting the font, sometimes it's uninstalling the package providing the font.

Did you install the fonts sometime in the past?
Did they come with your system?
Did they just magically appear one day?
Do you know the font names?

---

### Post by dino99 on 2015-06-14
you can first uninstall the fonts you dont want/need from the packages manager (mine is 'synaptic'; not installed by default)
then install localepurge (sudo apt-get install localepurge) and run it in a terminal to select the language you only want

---

