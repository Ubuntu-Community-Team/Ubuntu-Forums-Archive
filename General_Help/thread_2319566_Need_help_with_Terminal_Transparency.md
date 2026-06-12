---
title: "Need help with Terminal Transparency"
date: 2016-04-05
forum: General Help
---

### Post by bvdbsa on 2016-04-05
Good day all,

I would like to know if Ubuntu's unity desktop can achieve this(please note the attached screen shot below) I would like to see my desktop when I open/drag my terminal over open windows...

I am currently using Xubuntu but i would like to switch to the normal unity desktop, I am going to do a fresh install as soon as the new Ubuntu desktop releases later this April :D:o:D

So does anyone know if i can do it with a stock standard install or must i install other software like unity tweak tool or compiz.

PS: Ive never really used the unity desktop always use xfce.

Please let me know and thank you in advance.

---

### Post by howefield on 2016-04-05
Thread moved to the "*General Help*" forum.

---

### Post by pauljw on 2016-04-05
Open the terminal, go to 'edit; profile preferences' select background and set the transparency level you want.

---

### Post by bvdbsa on 2016-04-05
> **pauljw said:**
> Open the terminal, go to 'edit; profile preferences' select background and set the transparency level you want.

But that will only make terminal itself transparent? it wont allow me to see my desktop when i drag my terminal over other windows will it?

---

### Post by bvdbsa on 2016-04-05
> **bvdbsa said:**
> But that will only make terminal itself transparent? it wont allow me to see my desktop when i drag my terminal over other windows will it?

Here is a better example see that attached screen shot, my terminal is over my browser but it show my desktop instead of the browser in the background

---

### Post by pauljw on 2016-04-06
> **bvdbsa said:**
> Here is a better example see that attached screen shot, my terminal is over my browser but it show my desktop instead of the browser in the background

Hmmm.  I guess I'm not understanding what you want.  In the picture, are you just seeing a copy of the background loaded in the terminal or is the terminal peering thru the underlying app and displaying the actual background of the desktop?  If the former, on the same screen I pointed you to earlier, choose backgound image and select the matching background image that you use for the desktop.  If the latter, I have no idea how to accomplish that.

---

### Post by mcduck on 2016-04-06
So you actually want the fake transparency terminals used to have before compositing became possible, instead of real transparency you'd usually get these days?

(The fake transparency isn't really transparent, instead terminals copied your wallpaper image and then determined where the window is and which part of the wallpaper should be drawn as the terminal background)

Seeing that Gnome itself doesn't support any transaprency for Gnome-terminal any more and Ubuntu does some hacks to make it work on Unity desktop, I doubt swithcing to the old-school fake transparency is an option with gnome-terminal. However other terminal emulators might still do it. So, if the xfce-terminal you now has does that feature, then just use xfce-terminal in whatever desktop session you prefer...

---

### Post by vasa1 on 2016-04-06
> **mcduck said:**
> ...
Seeing that Gnome itself doesn't support any transaprency for Gnome-terminal ...
[s]Which version onwards doesn't support transparency? 1.3.8 still allows it. Pity if it'll be gone in 16.04 for those who aren't using Unity.[/s]I didn't take into account that compositing isn't to be used. gnome-terminal 1.3.8 has fake transparency. So does lxterminal.

---

### Post by Impavidus on 2016-04-06
> **mcduck said:**
> Seeing that Gnome itself doesn't support any transaprency for Gnome-terminal any more and Ubuntu does some hacks to make it work on Unity desktop, I doubt swithcing to the old-school fake transparency is an option with gnome-terminal. However other terminal emulators might still do it. So, if the xfce-terminal you now has does that feature, then just use xfce-terminal in whatever desktop session you prefer...

I remember seeing the fake transparency in xfce-terminal, but don't remember when was the last time I saw it. On Xubuntu 15.10 xfce-terminal just has real transparency [s]and I don't see any setting to change that[/s].

---

### Post by oldos2er on 2016-04-06
On my Xubuntu 15.10 the so-called fake transparency seems to be the default.

---

### Post by vasa1 on 2016-04-06
Just checked: on 14.04, xfce4-terminal has fake transparency.

---

### Post by Impavidus on 2016-04-07
Found it. In Xubuntu there is a checkbox to enable/disable the compositor in the settings for the window manager. So it's more like a property of the window manager than of xfce4-terminal. I only checked the terminal settings. I don't know about Ubuntu though.

---

### Post by vasa1 on 2016-04-07
> **Impavidus said:**
> Found it. In Xubuntu there is a checkbox to enable/disable the compositor in the settings for the window manager. So it's more like a property of the window manager than of xfce4-terminal. I only checked the terminal settings. I don't know about Ubuntu though.That's basically the same with lxterminal (Lubuntu) in 14.04 and also with gnome-terminal when installed in Lubuntu 14.04. Without compositing, all one can get is fake transparency. With compositing, one can get true transparency.

---

### Post by bvdbsa on 2016-04-08
Sorry if i wasnt clear but my terminal doesn't have a wallpaper set, my desktop background always shows where ever i go with my terminal, even when it moves open windows like my browser in the screen shot... I really hope i can find some tweak that allows me to do the same in ubuntu .... its the thing i love most of my terminal at the moment because when I use the terminal i dont have some application's text under it making the terminals text impossible to read unless i make it solid black:(

---

