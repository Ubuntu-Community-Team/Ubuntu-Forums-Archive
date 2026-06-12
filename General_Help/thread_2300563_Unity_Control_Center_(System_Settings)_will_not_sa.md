---
title: "Unity Control Center (System Settings) will not save display arrangement settings"
date: 2015-10-26
forum: General Help
---

### Post by Smask on 2015-10-26
Hi, this issue appeared when I upgraded to 15.10

I have two computers with dual screens and both are affected. I can arrange my displays OK, but when I reboot the computers they reverts back to the incorrect settings again. 
All my computers runs basic Ubuntu with flashback installed.

---

### Post by Smask on 2015-10-30
I've tested some further:

The Unity Greeter gets the settings wrong and when logging into Unity the settings get set in the correct position.
Logging into Flashback (Compiz or Metacity) doesn't load the settings. There is an old Display settings bug on Launchpad concerning Gnome DE (can't find it at the moment).

---

### Post by grahammechanical on 2015-10-30
Have you tried setting the settings in both Unity and Flashback? You will find that changing the settings in Flashback (Compiz) may mess up the same settings in Unity (Compiz) because you are changing the Compiz settings for both Flashback and Unity.

 You may also find that settings fixed in Unity (Compiz) do not have an effect in Flashback (Metacity) because the Metacity settings have not been changed. Compiz and Metacity are two different compositors/window managers. And so we can have two different arrangements of the user interface.

Regards

---

### Post by Smask on 2015-11-05
> **grahammechanical said:**
> Have you tried setting the settings in both Unity and Flashback? You will find that changing the settings in Flashback (Compiz) may mess up the same settings in Unity (Compiz) because you are changing the Compiz settings for both Flashback and Unity.

 You may also find that settings fixed in Unity (Compiz) do not have an effect in Flashback (Metacity) because the Metacity settings have not been changed. Compiz and Metacity are two different compositors/window managers. And so we can have two different arrangements of the user interface.

Regards

I have tried setting them logging in all three modes and it seems that logging into Flashback omits some steps. I have found a decent workaround by installing gnome-control-center and do the screen configuration there. Although the Unity Greeter still gets it wrong. (Booting up/logging back out)

---

