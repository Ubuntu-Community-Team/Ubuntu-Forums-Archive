---
title: "Kubuntu 13.04 Fonts Woes"
date: 2013-04-18
forum: General Help
---

### Post by jlacroix on 2013-04-18
I decided to check out Kubuntu 13.04. I was curious if the font issues that has historically plagued this distribution have been fixed but it seems not. I'll explain. If I change the fonts for KDE (System Settings > Application Experience > Fonts) there is basically no way to make the fonts look like they did when you first install Kubuntu. I've noticed this for several releases, and on several computers.

If I click the "Defaults" button, it changes the fonts back to the KDE defaults, not the defaults that Kubuntu ships with (the Ubuntu font).

If I try to change the fonts back manually (create a new user, write down the font settings, change the fonts in my account by hand) the fonts do not look anything like they did when I first installed Kubuntu.

Lastly, I notice that if I change the font settings, the fonts look extremely grainy and just plain bad. Changing the anti-aliasing and/or font DPI settings doesn't help either. I'm under the impression that there is no way to change the fonts back to the way they were shipped (which actually looks decent) without blowing away my .kde folder.

Has anyone else noticed this?

---

### Post by Gavin77 on 2013-04-18
I've never had any font problems here, they look good to me.

Here are the settings I use:

---

### Post by jlacroix on 2013-04-18
> **Gavin77 said:**
> I've never had any font problems here, they look good to me.

Here are the settings I use:
Thanks, that looks much better. It still doesn't look as good as a default Kubuntu install does out of the box, but good enough for me.

I'm very curious why the fonts never look the same if you customize them, even if you manually set everything back. I submitted a bug report for the fact that the defaults button in System Settings doesn't restore the Kubuntu defaults.

But if anyone wants to humor themselves, create a new user, take a picture of the System Settings screen where it shows the font settings, change your fonts to something else, log out, log in, change the fonts back, log out, log in and compare. You should see that the fonts look extremely pixelated and thin, unlike how it did when you first logged in as the new user. I'm not sure why but the Kubuntu defaults seem to be impossible to replicate.

---

### Post by Aide9aic on 2013-04-20
Here's my font configuration. I think they look quite nice. Perhaps you might try changing the hinting to *slight*; on every machine I've owned, this looked better than *medium* (of course, appearances are purely subjective).

[IMG]http://i.imgur.com/BkOECCg.png[/IMG]

My favorite font in the repository is DejaVu Condensed. When I'm building up a machine, I install that font package. Then I disable the standard ones, so that the Condensed versions become the DejaVu default.

[IMG]http://i.imgur.com/sUScAzp.png[/IMG]

You need to run **kdesudo systemsettings** to do this -- unelevated accounts can't enable or disable fonts. Right-click a font and choose **Disable** from the fly-out menu.

---

### Post by jlacroix on 2013-04-22
> **steveriley said:**
> Here's my font configuration. I think they look quite nice. Perhaps you might try changing the hinting to *slight*; on every machine I've owned, this looked better than *medium* (of course, appearances are purely subjective).

[IMG]http://i.imgur.com/BkOECCg.png[/IMG]

My favorite font in the repository is DejaVu Condensed. When I'm building up a machine, I install that font package. Then I disable the standard ones, so that the Condensed versions become the DejaVu default.

[IMG]http://i.imgur.com/sUScAzp.png[/IMG]

You need to run **kdesudo systemsettings** to do this -- unelevated accounts can't enable or disable fonts. Right-click a font and choose **Disable** from the fly-out menu.
Thank you, I'll give that a shot.

---

### Post by jlacroix on 2013-04-29
Thank you for posting your settings, I just now had a chance to try it out and it looks great!

---

### Post by Aide9aic on 2013-05-05
You're welcome. Glad it's working for you.

---

### Post by Bucky Ball on 2013-05-05
*Thread moved to **General Help**.*

As 13.04 is now released the Ubuntu +1 sub-forum is intended for Saucy so moving to here. ;)

---

### Post by speartip on 2013-05-05
Steve...
After reading this thread I followed your post & changed my fonts to Dejavu Sans Condensed, but there was absolutely no difference between the "book" font & the "condensed" font on my system (12.04).
Is this right??

---

### Post by Aide9aic on 2013-05-05
> **speartip said:**
> After reading this thread I followed your post & changed my fonts to Dejavu Sans Condensed, but there was absolutely no difference between the "book" font & the "condensed" font on my system (12.04).
Hm...which "book" font might you mean? The DejaVu family doesn't have a "book" type.

---

### Post by speartip on 2013-05-05
> **steveriley said:**
> Hm...which "book" font might you mean? The DejaVu family doesn't have a "book" type.

It does on my system??
DejaVu Sans has 10 font settings which include book & condensed, but both settings are identical.

---

### Post by Bucky Ball on 2013-05-05
> **speartip said:**
> It does on my system??


The OP is using 13.04 and you're using 12.04 LTS. Might be involved somehow.

---

