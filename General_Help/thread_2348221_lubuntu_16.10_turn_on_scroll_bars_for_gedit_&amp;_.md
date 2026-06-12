---
title: "lubuntu 16.10 turn on scroll bars for gedit &amp; dconf-editor"
date: 2017-01-01
forum: General Help
---

### Post by rccharles on 2017-01-01
I've installed lubuntu 16.10 [ running in a parallels VM ] I see scroll bars in Firefox, PCManFm, and Chromium.  I do not see scroll bars in gedit nor dconf editor.  I looked in the gedit preferences and didn't see a way to turn on scroll bars.  Haven't used gedit in a while so I could have missed the obvious. I tried this command:

gsettings get com.canonical.desktop.interface scrollbar-mode
No such schema 'com.canonical.desktop.interface'

no luck with dconf-editor 
the key doesn't exist: &#8220;ubuntu-overlay-scrollbars&#8221; from org -> gnome -> desktop -> interface

Should I try 2 or 3?
[http://ubuntuguide.net/turn-off-overlay-scrollbars-ubuntu](http://ubuntuguide.net/turn-off-overlay-scrollbars-ubuntu)

Perhaps if I know what all this meant, I could do something.
[https://launchpad.net/ubuntu/yakkety/+source/overlay-scrollbar](https://launchpad.net/ubuntu/yakkety/+source/overlay-scrollbar)

Robert

---

### Post by vasa1 on 2017-01-01
The GNOME project has "improved" how scrollbars appear and function in recent versions of GTK.

To get back to "legacy" scrollbars, add this line to your *~/.config/gtk-3.0/settings.ini*:
```
gtk-primary-button-warps-slider=false
```

I'll post some background links in a while.

Here's an oldish one: blogs.gnome.org/mclasen/2013/08/05/scrolling-in-gtk/

Each major GTK release is accompanied by a video: [https://www.youtube.com/user/GNOMEDesktop/videos](https://www.youtube.com/user/GNOMEDesktop/videos).

---

### Post by rccharles on 2017-01-02
The first image shows Machine information
[ATTACH=CONFIG]272994[/ATTACH]

Here is what I added.  The file didn't exist before I created it. 
[ATTACH=CONFIG]272993[/ATTACH]

Unfortunately, this didn't work as I had hoped.  I would like the scroll bars to always appear.  I had to move the mouse pointer into the section of the window with a scroll bar to see the scroll bar. 

Robert

---

### Post by vasa1 on 2017-01-02
As for your second image, if you didn't already have a *settings.ini* file, the first line of such a file should compulsorily be```
[Settings]
```with nothing else on that line.

So your entire settings.ini would then be```
[Settings] 
gtk-primary-button-warps-slider=false
gtk-long-press-time=5000

```
I have the "long-press" line which is supposed to fix some other scrollbar-related issue, I forget which.

If things still don't work for you, please try changing GTK themes. Do you know which theme you're using at the moment?


[center]****[/center]

Edit: also look at Toz' post here: [http://forum.xfce.org/viewtopic.php?pid=37175#p37175](http://forum.xfce.org/viewtopic.php?pid=37175#p37175)

I have that line:```
$ env | grep -i overlay
GTK_OVERLAY_SCROLLING=0
$
```

---

### Post by rccharles on 2017-01-03
Ok, somehow I got a scroll bar with gedit  :popcorn:  !
I did set a new theme, changed the ini file, and exported the variable in my .bashrc file.

Yeah, the black bar is a terminal image. 
[ATTACH=CONFIG]273005[/ATTACH]

I'll see if I can document exactly what I did later...

I'm running in Virtual Box now.  Parallels didn't let me use modifier keys like shift.  I'm trying things out so I can install Lubuntu on a friends machine.

---

### Post by vasa1 on 2017-01-03
Hi,
whenever you're posting textual content, it's preferable to post such content between quote tags (for general stuff) or between code tags (for terminal stuff). That way, it's easier for someone else to include what you've posted in their own posts in response to you.

For comparison, see how I posted the *get env | grep -i overlay* lines from my terminal.

[center]****[/center]
By the way, when using Lubuntu, an easier way to change themes (both widget and icon) and some other stuff is to use *lxappearance*: Menu > Preferences > Customize look and feel

---

