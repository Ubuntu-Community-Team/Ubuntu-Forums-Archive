---
title: "Is there a way to change slider color for better contrast"
date: 2018-06-03
forum: General Help
---

### Post by Ralph L on 2018-06-03
I recently installed Xubuntu 18.04 Bionic Beaver. For a variety of reasons (window grab edge too narrow, no stepper arrows, poor contrast between slider and slide background, etc.), I don't like the supplied themes, so I downloaded Clearlooks-Phenix.  This fixed most of my problems, but on certain applications such as Thunar (in particular, because I use it a lot), Appearance, Keyboard, Notes, etc. don't follow the Clearlooks theme in setting the color of the slider.  Is there a way that I can go into the system and set the slider color for those applications that don't follow the Clearlooks theme????  Or maybe I could set something in Clearlooks that would cause it to correctly set the slider color for those applications???

---

### Post by Ralph L on 2018-06-04
I fixed my own problem.  The sliders in all the apps are now blue as they should be.  I had installed Clearlooks-Phenix from [https://www.gnome-look.org/content/show.php?content=145210](https://www.gnome-look.org/content/show.php?content=145210) following the instructions in the Readme file.  This installed v7.0.1.  It turned out that Clearlooks-Phenix v7.0.1-1 for Bionic is available through the software repositories.  So I just used Synaptic to install it.  It also installed gtk2-engines (which the web site above recommended, but I forgot to do).  I had named my manually installed theme Clearlooks-Phenix, but the Synaptic installed version was named Clearlooks, so I now have both themes installed.  It must have been  the installation gtk2-engines that made the difference, because both themes now work correctly.  Incidentally going to Synaptic>Properties>Versions shows v7.0.1-1 as Bionic.

Hope this helps somebody....

---

### Post by Ralph L on 2018-06-04
I spoke too soon.  If I use Appearance to select Clearlooks-Phenix 7.1.0 (the one I manually installed from the Clearlooks website, after installation of Clearlooks-Phenix 7.0.1-1 and gtk2-engines) (using Synaptic), everything worked.  But if I used Appearance to select V7.0.1-1, then Firefox, Whiskers Menu, and other apps lose their stepper arrows. I want stepper arrows so I dropped back to V7.0.1.

---

