---
title: "Window behavior question"
date: 2019-09-25
forum: General Help
---

### Post by goemonburo on 2019-09-25
Sorry for the vague title, I don't exactly know what the right terms are for describing this.  But I use Lubuntu, 18.04LTS and have noticed that some windows can be right clicked on and I get options like "Send to desktop" or "Resize" or "Iconify" and so on.  Firefox behaves this way, OpenOffice, VNC, etc. 

However, other windows, such as Adobe Reader, do NOT allow any options when one right clicks.  I find the only way to move them to another virtual desktop is to drag them to the right or left of the screen, where they automatically move to the next virtual desktop over.  If I'm moving them one, it's fine, but it's cumbersome to move them repeatedly from vdesktop 1 to, say, vdesktop 8.  

Is there a way to force all applications to use that same window behavior?  Can I set this somehow in my preferences?  If so, is there a drawback in doing this, such as some applications will not function properly?

Any help would be greatly appreciated.

---

### Post by dragonfly41 on 2019-09-25
On Ubuntu 16.04 I have Docky installed. In Docky Settings > Docklets I have Workspace Switcher installed.
I right click on top bar of any window and I can move to any virtual workspace.

---

### Post by goemonburo on 2019-09-25
Thank you, I'll look into Docky.  I'm mainly curious WHY there's a difference between certain applications in their window behavior.  Just seems so random yet there must be a reason why certain applications are fine and others don't have the same right-click behavior.  

But Docky may be the solution I need.  Thank you!

---

### Post by CatKiller on 2019-09-25
You should be aware that Adobe Reader was abandoned in 2013. There are better, and actually supported, PDF viewers installed by default already in Gnome (evince) and KDE (okular), although I don't know that LXDE/LXQt has its own.

Which other applications are you running that don't work with your window manager?

---

### Post by Impavidus on 2019-09-25
Another suggestion (I'm on Xubuntu, but I think all DEs are similar in this respect), I've arranged my desktops in a 3 by 5 grid, wrapping at the edges, so I can get from any of my 15 desktops to every other in at most three steps. And I use ctrl+alt+shift+arrow to move the active window from one desktop to the other. ctrl+alt+arrow just moves the view, not the window.

---

### Post by goemonburo on 2019-09-25
Sure, I am aware, @catkiller. Adobe Reader isn't the only application with this behavior though.  Just happened to have that in mind.  Do you think that it's only an issue of supported applications?  I hadn't thought that, but can certainly keep that in mind when I notice it in other apps.  If any other thoughts come to mind please let me know.

---

### Post by Holger_Gehrke on 2019-09-26
A window's title bar and borders are drawn and managed by the window manager and not by the program itself. Interactions with these parts of a window are also handled by the window manager. On LUbuntu that should be openbox unless you changed it. openbox can be configured to treat windows that match various criteria in some special way, like forcing the window to go to a specific desktop or always come up at a specific size or ... . Check your openbox configuration, either the global one in /etc/xdg/openbox/rc.xml or -- if you have one -- the personal one in ~/.config/openbox/rc.xml. Documentation for the format of that file can be found at [http://openbox.org/wiki/Help:Configuration](http://openbox.org/wiki/Help:Configuration)

Holger

---

### Post by goemonburo on 2019-11-21
So interestingly enough, this is NOT actually happening with Adobe Reader after all, which turns out isn't installed at all.  It is Evince.  Which one would expect to conform to the standards set by the window manager.  No?  In this case, right clicking on every other window (VLC, Xterm, Firefox, Okular) will elicit a pull down menu with a "Move to desktop..." option.  However with Evince (and as I said, a few other programs, though none come to mind) it does not offer me that.  The window LOOKS different too -- thicker, with a underscore, single square, and x in the upper right.  Whereas all other windows have a narrower bar across the top and an underscore, double square (smaller and larger), and x.  

I feel like this program is somehow overriding the windowmanager, maybe?  Using a different one?  Instead of the one supplied by the theme?!  If so, why?  And how can I force it to stop this ridiculous and insolent behavior?  :-)

---

### Post by CatKiller on 2019-11-21
> **goemonburo said:**
> However with Evince (and as I said, a few other programs, though none come to mind) it does not offer me that.  The window LOOKS different too -- thicker, with a underscore, single square, and x in the upper right.  Whereas all other windows have a narrower bar across the top and an underscore, double square (smaller and larger), and x.  

I feel like this program is somehow overriding the windowmanager, maybe?  Using a different one?  Instead of the one supplied by the theme?!  If so, why?  And how can I force it to stop this ridiculous and insolent behavior?  :-)

So if it's only Gnome-native applications (like Evince) that have that issue, then it's possible that they're using client-side decorations, where the application can go with wherever whims it likes regardless of how the window manager does things. I don't use Gnome, so I couldn't tell you how to make them stop doing that.

---

### Post by Impavidus on 2019-11-21
Some applications are different, indeed: evince, document scanner, calculator. They have a different look (rather ugly) than most other applications on my Xubuntu system and there seems to be no way to configure that look. Even the rare Qt-application I use has a consistent look with the other Xubuntu stuff. However, even evince has the menu with an option to send it to a different workspace when I rightclick on the title bar. I never use that option though, as stated above I use the keyboard to move windows from one workspace to the other.

---

### Post by CatKiller on 2019-11-21
Apparently there is something called **gtk3-nocsd** which might help in some fashion. Like I said, I don't use Gnome so I don't use Gnome applications.

---

### Post by goemonburo on 2019-11-21
@Impavidus, what are the key commands you use for that?  Is it Xubuntu-only?  I wouldn't mind doing that as a work around when I need to.

---

### Post by goemonburo on 2019-11-21
@CatKiller, thank you for the info...I'll look into that and see if it helps!

---

### Post by goemonburo on 2019-11-21
@CatKiller, thank you for the info...it seems that hack worked!  Great to know about.  I wish I could somehow make it automatic for opening those particular applications.  But this is probably all I need for now.  Much appreciated!

---

### Post by Impavidus on 2019-11-22
> **goemonburo said:**
> @Impavidus, what are the key commands you use for that?  Is it Xubuntu-only?  I wouldn't mind doing that as a work around when I need to.

shift+ctrl+alt+<arrow key>. I don't know if this is Xubuntu-specific, but I think I used the same key combo before I switched to Xubuntu, so that was under the old gnome 2 of Ubuntu 10.04. In any case, in Xubuntu it's configurable to any key combo you like. There are also key combos to jump to a non-adjacent workspace directly. It's all in the window manager settings. Now I heard that the xfce4 desktop environment is a lot more configurable than gnome, so that may be less easy on your system.

I found key combos much faster than menus. It takes time to reach for the mouse.

---

### Post by ajgreeny on 2019-11-22
I'm not on my LXDE machine at the moment (Debian-10-LXDE) on an old netbook, so can't check this but in openbox-settings (or whatever it's called) you may find something that will help you get what you want with keyboard shortcuts.

---

### Post by CatKiller on 2019-11-22
> **goemonburo said:**
> @CatKiller, thank you for the info...it seems that hack worked!  Great to know about.  I wish I could somehow make it automatic for opening those particular applications.  But this is probably all I need for now.  Much appreciated!

Glad to hear it worked. 

The launchers for each application, and for using an application for automatically opening a particular file, are just text files. You could edit them to change the "Execute=" line. 

Or switch to non-Gnome equivalents like okular. AFAIK it's only some Gnome devs that think that client-side decoration is a good idea rather than a complete abomination.

---

