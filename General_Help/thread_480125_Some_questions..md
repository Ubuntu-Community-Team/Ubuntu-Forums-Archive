---
title: "Some questions."
date: 2007-06-21
forum: General Help
---

### Post by LiNuXxToOthEMaX on 2007-06-21
im new to ubuntu and i dunno how to play mp3s

1. how do i play mp3's
2. any good burning programs
3. anything faster than Firefox?
4. desktop effects

any ideas?

thanks in advance.

---

### Post by Crafty Kisses on 2007-06-21
> **LiNuXxToOthEMaX said:**
> im new to ubuntu and i dunno how to play mp3s

1. how do i play mp3's
2. any good burning programs
3. anything faster than Firefox?
4. desktop effects

any ideas?

thanks in advance.

1. Install the plugins from "AutoMatix" or some other program like that.
2. K3B is pretty decent.
3. "SwiftFox" is an optimized version of FireFox
4. You might want to try Compiz or Beryl.

How to download "AutoMatix and "K3B"

AutoMatix
```
sudo-apt-get install automatix2
```

K3B

```
sudo apt-get install k3b
```

Hope this helps. :p

---

### Post by tkjacobsen on 2007-06-21
1. how do i play mp3's
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) -- Remember to read the legal notice

2. any good burning programs
gnomebaker in gnome -- k3b in kde (I think this is the best, and it also works in gnome, but the interface is kde)

3. anything faster than Firefox?
epiphany in gnome (epiphany-browser in synaptic)
konqoeror in kde

4. desktop effects
gnome:
system -> administartion -> restricted manager 
system -> preferences -> dekstop effects

---

### Post by tkjacobsen on 2007-06-21
> **Codename said:**
> 1. Install the plugins from "AutoMatix" or some other program like that.

Please take care when using automatix or avoid it if possible. It is discouraged by the ubuntu devs as it is known to break your upgrade chain...

Use Add/Remove instead (most apps are there -- ask here for the rest)

---

### Post by kevinlyfellow on 2007-06-21
3.  Dillo, Opera, Galeon, [Swiftweasel]("http://swiftweasel.sourceforge.net/")

I agree that you should probably refrain from automatix, I've been neutral until I tried to help someone fix their problems after they used it.  Also, the maintainer of Swiftfox is a bit on the sketchy side when it comes to honouring the licenses.  Swiftweasel is the same thing, just without the legal questions.

---

### Post by Crafty Kisses on 2007-06-21
> **kevinlyfellow said:**
> 3.  Dillo, Opera, Galeon, [Swiftweasel]("http://swiftweasel.sourceforge.net/")

I agree that you should probably refrain from automatix, I've been neutral until I tried to help someone fix their problems after they used it.

I haven't had all that much trouble with "AutoMatix" only with the Video Card drivers, which I will never use it for that again, but for everything else I think it works really good, but that's just me I guess.

---

### Post by kevinlyfellow on 2007-06-21
I used it once, and generally things were ok (it was when it was just released).  But when things become a mess, they can be bad.  I was trying to have someone install a simple media player and it was insane.  Dependencies were failing left and right...  But, I guess it really is about what you install with it that matters.

---

### Post by tkjacobsen on 2007-06-21
> **Codename said:**
> I haven't had all that much trouble with "AutoMatix" only with the Video Card drivers, which I will never use it for that again, but for everything else I think it works really good, but that's just me I guess.

It's not that Automatix doesn't work at all. I would just recommend to use the tools included in ubuntu whenever possible to be on the safe side. That is for video drivers, codecs! and installation of most applications. (All problems in this thread)

---

### Post by dead_end on 2007-06-21
Avoid AutoMatix if possible. 

1. Search the community docs for either "restricted formats" or "mp3"
2. K3b seems to me to be the best, although I haven't had any trouble with Gnome baker
3. dillo I can run it on a 533mhz with 56 megs ram no problem.
4. if fiesty go to the menubar click System > Preferances > Desktop effects.

WARNING:: Desktop effects are in testing and might mess up your desktop.

---

### Post by sloggerkhan on 2007-06-21
1. Use the repositories. I think even the ADD/Remove menu in Feisty has an entry for restricted codecs, flash player, java, that sort of thing.
2. I agree with K3B (it's the only KDE app I really use)
3. User preference.
4. Other notes are right.

Side notes:
Might want to look at VLC as a media player.
I am a fan of Thoggen for DVD ripping/encoding, but there are other choices with more options.
My own opinion on torrent clients for Ubuntu is that Deluge is best. (Though it's still in development.)
OpenArena is a kinda fun casual FPS.

---

### Post by kevinlyfellow on 2007-06-21
1) If you are using feisty fawn (the latest ubuntu), just double click an mp3 and it will walk you through the installation.  There are plenty of ways to skin that cat...

3) Another thought, I've noticed Seamonkey is now faster than firefox

---

### Post by Crafty Kisses on 2007-06-21
> **tkjacobsen said:**
> It's not that Automatix doesn't work at all. I would just recommend to use the tools included in ubuntu whenever possible to be on the safe side. That is for video drivers, codecs! and installation of most applications. (All problems in this thread)

Yep, I see where you're coming from. ;)

---

