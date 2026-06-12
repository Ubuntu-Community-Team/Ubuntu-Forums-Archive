---
title: "Ubuntu stuck at boot screen."
date: 2013-03-28
forum: General Help
---

### Post by captainwithershins on 2013-03-28
So Ubuntu broke again :(. I installed the official AMD drivers for my video card. Everything was nice but the update said that there were broken packages fglrx. Weird because there was no graphics update or atleast an AMD one. I scrolled through the updates and I saw something very odd. It wanted to install Nvidia drivers. I deselected them, but it still said that there were broken packages. I left it like that for a day and then decided to just force it sudo apt-get -f install or something like that. It updated and I was happy until restart. When I restarted Ubuntu was stuck at the screen with the 5 red dots and the Ubuntu name on top. Any ideas?

---

### Post by JLeon85 on 2013-03-28
If you still have your install disk you might want to try booting into nomodeset through F6 on the main install menu. That should at least get you in there, and then you can sort out the driver issue from there.

---

### Post by captainwithershins on 2013-03-29
I got in the CD. I'm at the menu tbat asks you to try or install. Pressing F6 doesn't do anything. What am I doing wrong?

---

### Post by captainwithershins on 2013-03-29
Nevermind. Fixed it by removing the nvidia driver from the root terminal in the recovery menu.

---

### Post by JLeon85 on 2013-03-29
Ok. Btw, this was the screen I was referring to. 


[IMG]http://ubuntunigeria.files.wordpress.com/2007/09/bootscreen1.jpg[/IMG]

---

