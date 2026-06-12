---
title: "Binding the &quot;window key&quot; to open the menu?"
date: 2006-07-07
forum: General Help
---

### Post by boom2k1 on 2006-07-07
In windows, when you press the windows key, the "Start" menu from the taskbar would expand.

How do you imitate this effect in ubuntu?

Thanks

---

### Post by aysiu on 2006-07-07
Are you in KDE or Gnome?

---

### Post by boom2k1 on 2006-07-07
Thanks.

Nevermind, I figured this out!

In GNOME, I would do the following:

System->Preference->Keyboard Shortcut--> 

In Desktop, find "Show the panel menu" and assigns the windows key. :)

---

### Post by Bloch on 2006-07-07
I bind it to make windows go fullscreen. People think it's cool. It's been so long snce I used windows I can't remember if you can make a window go fullscreen, and the low-IT friends I have don't know.

---

### Post by aysiu on 2006-07-07
Full-screen... or maximized?

I don't know about full-screen, but I wish Windows had a keyboard shortcut for maximizing Windows. As it is, at work, when I want to maximized stuff in XP, I have to do Alt-Spacebar to get a context menu up for the window, then press X to get it maximized.

---

### Post by chrsjav on 2006-07-07
For some reason I can't combine the windows key with any other key.  I can easily use, say <Ctl><Alt><L> to lock the screen, but the keyboard shortcut app won't let me use <Super_L> with anything else!

Should I file a bug?

By the way I LOVE the new forum layout. :D

---

### Post by yabbadabbadont on 2006-07-07
It sounds like a bug to me.  You can use that key with others in fluxbox.

---

### Post by aysiu on 2006-07-08
You have a choice. It can be its own key. Or it can be a modifier key. You can switch back and forth between the two at System > Preferences > Keyboard. But you can't have both at the same time.

---

### Post by ash211 on 2006-07-08
That's one of the few things that I miss from XP.  KDE actually has a better replacement feature, in my opinion.  Usually, the start menu is used to open programs, but a program called katapult can do it easier.  Just hit alt-space and type the first few letters of the program you want to open and hit enter.  The program opens, and katapult melts back away to the system tray.  It's that simple!

---

### Post by aysiu on 2006-07-08
Well, Alt-F2 will bring up the Run dialogue, and you can usually do the first few letters and autocomplete... in both Gnome *and* KDE.

---

### Post by GenPFault on 2006-07-12
> **aysiu said:**
> You have a choice. It can be its own key. Or it can be a modifier key. You can switch back and forth between the two at System > Preferences > Keyboard. But you can't have both at the same time.
Is this an X Windows bug or a Gnome/KDE bug?

---

### Post by aysiu on 2006-07-12
It's not really a bug.

I don't think Gnome has ever wanted to implement a hybrid functionality for the Windows key.

KDE used to have it but decided against it for stability reasons.

**Edit**: Sorry, it's not stability. It's something else: > Previous versions of KDE provided a trick to allow you to use the Windows® key both as a modifier (so you could have shortcuts like Win+R), and as a regular key (so that pressing Win on its own could open the K menu). This feature was removed for reasons of usability and accessibility, as well as keeping the code clean. For current versions of KDE, you have two options: either use a different shortcut to open the K menu (the default is Alt+F1), or remap the Win key to be a regular key, rather than a modifier. [http://docs.kde.org/stable/en/kdebase/faq/panel.html#id2552351](http://docs.kde.org/stable/en/kdebase/faq/panel.html#id2552351)

---

### Post by GenPFault on 2006-07-12
> **aysiu said:**
> It's not really a bug.

I don't think Gnome has ever wanted to implement a hybrid functionality for the Windows key.

KDE used to have it but decided against it for stability reasons.

**Edit**: Sorry, it's not stability. It's something else:  [http://docs.kde.org/stable/en/kdebase/faq/panel.html#id2552351](http://docs.kde.org/stable/en/kdebase/faq/panel.html#id2552351)
So it is a window manager problem.  Now I know who to complain to/what to attempt to fix.  Thanks!

---

### Post by HAARP on 2006-07-12
> **aysiu said:**
> Well, Alt-F2 will bring up the Run dialogue, and you can usually do the first few letters and autocomplete... in both Gnome *and* KDE.

When I press tab in that launcher on Gnome, it won't autocomplete. Instead, it jumps from button to button. How do you do it?

---

### Post by aysiu on 2006-07-12
I don't press Tab. I just start typing the first few letters.

---

### Post by HAARP on 2006-07-12
Doesn't do anything. Do I need to type as much as to uniquely identify the command?

---

### Post by aysiu on 2006-07-12
In Gnome, yes, you need to type enough to uniquely identify the command. Then it'll fill in the rest.

In KDE, you type only a little bit, and the list of possible guesses pops up in a drop-down menu underneath.

I believe Gnome's autocomplete is a true autocomplete and KDE's autocomplete is based on commands you've previously typed in.

---

### Post by HAARP on 2006-07-12
In this case, I prefer bash (Alt+F3)
Has this nifty suggestions-feature :p 
Thanks anyway

---

### Post by ciscosurfer on 2006-07-27
You can add KDE's drop-down-like menu set to a run dialog by issuing the following command in a terminal using gconf (or use the gui for  gconf, the configuration editor)```
gconftool -t bool -s /apps/panel/general/show_program_list true
```

---

