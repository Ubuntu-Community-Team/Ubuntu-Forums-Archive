---
title: "Upgrade to 12.04 freezing after login"
date: 2014-02-24
forum: General Help
---

### Post by ufarmer on 2014-02-24
I just upgraded my Lenovo ThinkPad T500 from 10.04 to 12.04 and I am experiencing constant freezes and the occasional crash.  Usually, I am still able to move the cursor using the touchpad while not being able to click on anything.  Sometimes even the cursor is frozen.  So far, I can always open a terminal using the keyboard commands.

I have googled and googled and tried everything I could find, all with no luck.  Any advice is appreciated.

---

### Post by Xanthius on 2014-02-24
First of all, I am not an experienced Linux as I've just started to get the hang of it. But since any advice is appreciated..

I would not dare to say how the "upgrade" progress of Linux works, but if its anywhere near Microsoft's one I'd *definitely* try a clean install first, or make a bootable usb drive and run it from it.
The reasoning is mainly the drivers being forwarded to the new version, but lots of things have changed from 10.04 to 12.04 so perhaps it is causing the issue (mainly your display driver)

Futhermore, you state constant freezes meaning your cant use your computer at all with unity? You might want to change to the alternate unity display manager which can be done in the login screen.
I believe it was Unity2d and normal unity. 

When it's happening intermittently, and not constantly you can also switch to a tty console, login and type "sudo restart lightdm". Perhaps it works and you dont need to restart your entire computer anymore.

---

### Post by ufarmer on 2014-02-24
After much freezing, crashing, and some overheating (!!!), everything is working properly now.  And since the OS kept freezing, this is not due to any changes I made since I couldn't make any.

I wanted to avoid a clean install since I have been using my laptop as my main working computer for years and I have made many, many customizations.  However, I was gearing up for one before things mysteriously settled down.  I might still do it though.

---

