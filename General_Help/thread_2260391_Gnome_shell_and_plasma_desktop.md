---
title: "Gnome shell and plasma desktop"
date: 2015-01-11
forum: General Help
---

### Post by tonev on 2015-01-11
As the title says I am running both gnome shell and plasma desktop but i got a problem. The plasma desktop does not save it's setting for example the wallpaper and what widgets are on the desktop etc.  I installed the desktop by using apt get install command and installing plasma-desktop. Then i run it via alt+ f2 and typing plasma-desktop : ) I am running the latest version of ubuntu gnome : )

---

### Post by ajgreeny on 2015-01-11
You need to set the DE of a session from session start by clicking on the options icon of the login screen, not by running the command you are using.

Try doing things that way, and come back again if the problem persists.

---

### Post by tonev on 2015-01-11
But this way i am not running the gnome shell and the plasma desktop at the same time. I want to run them both at the same time. I have noticed that some of the settings are remembered like for example the theme settings and the fact hat i have removed all the panels but it does not remember my wallpapers settings and my widget placement.

---

### Post by ajgreeny on 2015-01-11
I am not aware that you can run the two together at the same time; I may be wrong, however, so wait to see if more answers come along to help you out on this, as I could be wrong.

---

### Post by deadflowr on 2015-01-11
So I saw this and decided to try it out on a spare machine.
What is happening is you can indeed run both desktops at once, though it looks really weird.
But you can only log out through the gnome-shell logout and not the plasma-desktop logout.
Since you are not logging out of plasma it's settings are not saved.

**Edit**: A quick realization occurred when I remembered to look at what current desktop session I was in
```
echo $DESKTOP_SESSION
```
which outputs gnome.
Meaning that plasma-desktop is not a running session, but rather simply a desktop running on top of the current gnome-shell session. Since no plasma-desktop session is/was ever running, to put it bluntly, how could it ever hope to save a session that never actually existed.

---

### Post by tonev on 2015-01-11
So if i save my session in the kde desktop and run the kde desktop in gnome it will be all saved ?

---

### Post by tonev on 2015-01-17
No it does not save them even if i do save them I log in to the plasma desktop.

---

### Post by tonev on 2015-01-27
Well anyone? I really like having the gnome look and the kde desktop widgets : )

---

### Post by monkeybrain20122 on 2015-01-27
Why would you want to run them at the same time? I would be very surprised if you don't get into troubles.

---

### Post by deadflowr on 2015-01-27
I don't think it produces as much troubles as it does simply being completely weird.
Indeed you could/should expect a decent amount of hard times, but you can set it to have a somewhat functional system.
The biggest obstacle I found was that each fights for the common areas, like panel space.
I would never use or recommend anyone use it for their daily driver, it's simply superbloat.
Like over-the-top superbloat.


Having stated that, I think if you use the --config option when launching plasma-desktop, you can have it load a customized config file.
```
plasma-desktop --config filename-here
```
But I have no idea what you would put into that file.
I would assume you could have it load a theme and a wallpaper, if you like.
Unfortunately, again, I have no idea how you would write the file.

So, in the end, I'm probably not being very helpful.:(

---

### Post by monkeybrain20122 on 2015-01-27
> **deadflowr said:**
> I don't think it produces as much troubles as it does simply being completely weird.
Indeed you could/should expect a decent amount of hard times, but you can set it to have a somewhat functional system.
The biggest obstacle I found was that each fights for the common areas, like panel space.
I would never use or recommend anyone use it for their daily driver, it's simply superbloat.
Like over-the-top superbloat.


And which controls the desktop, whether nautilus or Dolphin controls file and what happens when you plugin a usb... I can think of many problems.

---

### Post by deadflowr on 2015-01-27
> **monkeybrain20122 said:**
> And which controls the desktop, whether nautilus or Dolphin controls file and what happens when you plugin a usb... I can think of many problems.

Neither, because gnome-shell and plasma-desktop do not have the file manager handle the desktop.
(Or at least I've seen nothing to indicate otherwise that plasma-desktop does not have the file manager handle the desktop)
Unlike desktops such as Unity.
But gnome-shell was built to be extremely independent. And as such was designed to be able to run without the need to have a file manager handle the desktop.

And unless you purposely install dolphin(which does not get pulled in when you install plasma-desktop), the file manager would be nautilus.

---

