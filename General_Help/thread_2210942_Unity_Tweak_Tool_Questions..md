---
title: "Unity Tweak Tool Questions."
date: 2014-03-13
forum: General Help
---

### Post by Roasted on 2014-03-13
Hello friends. I dug around online but I couldn't find much reference about this. It seems as if most poeple just install Unity Tweak Tool and run with it since it works. But I'm curious about what it actually does under the hood. Is it just editing dconf settings? 

For example, let's say I wanted to adjust the transparency level of the top Unity bar where the clock is, etc. In Unity Tweak Tool, I'd go to Panel >> Transparency Level. But what is it doing? How could I do this without Unity Tweak Tool if I so desired?

---

### Post by mcduck on 2014-03-13
You got it right, it's just collecting various dconf keys and other settings, plus some simple scripts and other tools into one GUI to make things easier. All the same things can be done without the tweak tool if you don't want to install it and are willing to dig into the settings yourself.

For example the panel transparency is controlled by the *org.compiz.unity.plugns.unityshell.panel-opacity* key, and can be changed using dconf-editor or gsettings command.

---

