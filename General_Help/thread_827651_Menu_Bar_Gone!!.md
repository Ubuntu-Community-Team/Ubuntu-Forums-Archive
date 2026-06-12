---
title: "Menu Bar Gone!!"
date: 2008-06-13
forum: General Help
---

### Post by spraveenitpro on 2008-06-13
Hi 

My Entire Menu bar consisting of 'places,system,preferences' and the task bar have disappeared. I am unable to launch any program or do anything. only the wallpaper shows up. Alt-f2 also does not work.

praveen.

---

### Post by ajmorris on 2008-06-13
Hi there,
this is most likely caused by an application starting at startup, that is not being sub-tasked properly.
You might have to manually edit some files in ~/.gconf  (alternatively you could backup the contents, and delete them, and have gnome regenerate this folder automagically, but that would mean that any gnome application you use, would lose its configuration options)

AJ

---

### Post by iaculallad on 2008-06-13
Press Ctrl+Alt+F1, this brings you to your terminal:

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

then press Ctrl+Alt+F7 to go back to your GUI.

---

### Post by ajmorris on 2008-06-13
> **iaculallad said:**
> Press Ctrl+Alt+F1, this brings you to your terminal:

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```then press Ctrl+Alt+F7 to go back to your GUI.

If you do this, you lose all configuration that you have done, so, you might like to back up these first, to slowly migrate back your configuration, to see what the issue was

---

### Post by cc8balla on 2008-06-13
Yea, telling someone to use rm, without them knowing what it means (sorry if you do, OP, just trying to make a point), is NOT a good idea.

---

### Post by wersdaluv on 2008-06-13
If you have gnome-do installed, open the "Login Window" dialog using it. If you don't login using another user account (if you have one) then edit your config files

---

### Post by spraveenitpro on 2008-06-14
Hi All

Nothing seems to work, tried deleting all the gconf files and rebooting , still same, menu bar doesnt show up...only wall paper!
Why does the menu bar not load, how can i see the startup apps in ubuntu...thanks..

praveen

---

### Post by ajmorris on 2008-06-14
> **spraveenitpro said:**
> Hi All

Nothing seems to work, tried deleting all the gconf files and rebooting , still same, menu bar doesnt show up...only wall paper!
Why does the menu bar not load, how can i see the startup apps in ubuntu...thanks..

praveen

It has been a while since i used gnome, but, if i remember correctly, you can run gnome-session or gnome-session-properties to set what is started at gnome startup. You could try stopping everything there from starting up, and seeing if that helps. Another alternative could be to re-install gnome itself.

AJ

---

### Post by supergenius23 on 2008-06-14
> **ajmorris said:**
> It has been a while since i used gnome, but, if i remember correctly, you can run gnome-session or gnome-session-properties to set what is started at gnome startup. You could try stopping everything there from starting up, and seeing if that helps. Another alternative could be to re-install gnome itself.

AJ

I am also having the same problem... all of a sudden I could not click on any menu bar and when I restarted, the bars did not load. 

How do I go about re-installing gnome itself?

---

### Post by ajmorris on 2008-06-14
> **supergenius23 said:**
> I am also having the same problem... all of a sudden I could not click on any menu bar and when I restarted, the bars did not load. 

How do I go about re-installing gnome itself?

If you use synaptic or a variation there of, you can just find the ubuntu-desktop package, and mark it for re-install.
if you use the command line, you can do ```
sudo apt-get remove --purge ubuntu-desktop && sudo apt-get install ubuntu-desktop

```

The ubuntu-desktop package is a meta-package that pulls down all gnome dependencies ( just like there are edubuntu-desktop, edubuntu-desktop-kde, kubuntu-desktop, xubuntu-desktop packages which are the same, but for their respective DEs)

AJ

---

### Post by mark36ph on 2008-06-15
Thanks, My desktop died last night but that last post fixed it for me.

Thank you.

---

### Post by Atean_Linux on 2008-06-28
> **spraveenitpro said:**
> Hi 

My Entire Menu bar consisting of 'places,system,preferences' and the task bar have disappeared. I am unable to launch any program or do anything. only the wallpaper shows up. Alt-f2 also does not work.

praveen.


This is a simple mistake done by the best of us at first. Do not panic. And you don't have to go through any configurations either.


Simply right-click on the desktop and click on 'create a launcher'.

Make the command "gnome-panel", and when you click on this launcher the panel will load back up.
Then you can delete the launcher.


Good luck on your explorations! That's what Linux is all about.

---

