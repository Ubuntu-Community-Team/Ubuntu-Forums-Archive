---
title: "does gnome show window titles or not?? with alt tab"
date: 2016-11-05
forum: General Help
---

### Post by linuxhard on 2016-11-05
does gnome show window titles or not??

--> [https://ubuntuforums.org/showthread.php?t=2342235&p=13565880#post13565880](https://ubuntuforums.org/showthread.php?t=2342235&p=13565880#post13565880)

[COLOR=#000000]hi, i really really need someone to recommend something that shows the titles of the windows on the window switch screen -- jsut like it does on windows[/COLOR]

[COLOR=#000000]any desktop[/COLOR]
[COLOR=#000000]any os[/COLOR]
[COLOR=#000000]anything[/COLOR]

[COLOR=#000000]really really need help.... so i can FINALLY use ubuntu... [/COLOR]

[COLOR=#000000]it's the first & BIGGEST problem i have

 [/COLOR][h=2]{16.04} alt tab show title of windows on window switch screen[/h]

---

### Post by CantankRus on 2016-11-05
Need a bit more info with this...not sure what you mean.

---

### Post by CantankRus on 2016-11-05
The default switcher will show titles of grouped windows as cycled.
Press alt+tab to grouped windows and after a short delay window previews will show.
While still holding down alt, use the tilde(~) key to cycle through grouped windows.
[ATTACH=CONFIG]271991[/ATTACH] [ATTACH=CONFIG]271992[/ATTACH]

You can also install extra compiz plugins where you can try other switchers
like the ring switcher
[ATTACH=CONFIG]271993[/ATTACH]

or shift switcher
[ATTACH=CONFIG]271994[/ATTACH]

Install compiz-plugins and compizconfig-settings-manager(ccsm) via terminal...
```
sudo apt install compiz-plugins compizconfig-settings-manager
```
 
In the dash search for ccsm where you can try different switchers and settings.
[ATTACH=CONFIG]271995[/ATTACH]

Settings for the default alt+tab switcher are in ccsm > ubuntu unity plugin > switcher

The scale windows plugin (Super+w) and alternate switchers should all show window titles but need the **ccsm > image loading > text plugin** enabled.

....and when you completely stuff up your compiz settings, run this terminal command to set back to default...
```
dconf reset -f /org/compiz/
```

---

### Post by linuxhard on 2016-11-06
i posted a pic of the 'task view' in windows 10 but i guess it was too large so someone deleted it

it only shows the title of the active alt tab selection, it doesnt show all window titles,

any fix for this? any desktop, os, etc. really needed

---

### Post by CantankRus on 2016-11-06
The **scale addons** plugin has a setting to show titles for all windows.

Using ccsm, enable the **scale addons**, and **text **plugins.
Then set the window title display options in ccsm  > scale addons > appearance.
Use the scale shortcut key...Super+w.
Super is the Windows key but we don't like to give Windows it's own personal key here.

Forums not letting me attach pictures at the moment...will try a bit later.

---

### Post by linuxhard on 2016-11-06
super w doesn't function like alt tab or alt ~

that was the specific need, links fully express the problems / limits

---

### Post by CantankRus on 2016-11-06
Well that's about all I got on your "specific needs".
Good luck.

---

### Post by linuxhard on 2016-11-06
well that sucks, hopefully someone else knows a solution

windows macos (95+% of os market) both can do this basic thing --

[http://askubuntu.com/questions/845370/16-04-alt-tab-in-gnome-switch-between-all-non-minimised-windows-in-a-single-a](http://askubuntu.com/questions/845370/16-04-alt-tab-in-gnome-switch-between-all-non-minimised-windows-in-a-single-a)
[https://news.ycombinator.com/item?id=12853531](https://news.ycombinator.com/item?id=12853531)

---

### Post by Dennis N on 2016-11-06
> **linuxhard said:**
> i posted a pic of the 'task view' in windows 10 but i guess it was too large so someone deleted it it only shows the title of the active alt tab selection, it doesnt show all window titles, any fix for this? any desktop, os, etc. really needed
Xubuntu's alt-tab switcher will display the window titles (if any) on all desktops. See attached image. Maybe this is what you have in mind. (Not familiar with Windows and its switcher - sorry).

---

### Post by linuxhard on 2016-11-06
if you google 'task view' 

then pick the 'images' tab of google site

you can see how the window switch screen looks like

i was just about to ask on the xfce forum

---

### Post by Dennis N on 2016-11-06
> **linuxhard said:**
> if you google 'task view' 

then pick the 'images' tab of google site

you can see how the window switch screen looks like

i was just about to ask on the xfce forum

Ok, I looked at the images. Xubuntu (or any XFCE desktop system) has two alt-tab switcher display modes - list mode (my screenshot in previous post) and preview mode. List mode shows the titles on all the windows. There is also a preview mode (like the Windows images) but this only shows the window title when it is selected*. The fact that list mode shows the titles, and also is more compact, is why I use the list mode myself. Either mode can be set to cycle through all desktops, or only the current desktop.

I didn't check LXDE or MATE desktops (not at hand right now). I can check later.

* window title is shown at bottom of the switcher.

---

### Post by linuxhard on 2016-11-06
[http://www.extremetech.com/wp-content/uploads/2015/08/TaskView2.jpg](http://www.extremetech.com/wp-content/uploads/2015/08/TaskView2.jpg)

* how about the showing only the non-minimised windows like how macos does it? (on the askubuntu links)
** i think windows has an addon for this, haven't finished checking
* assuming the other desktops also doesn't show windows titles (macos doesn't either)

---

### Post by coffeecat on 2016-11-06
@linuxhard, please be mindful of those with limited bandwidth and those using mobile devices to browse the forum by not posting giant images hosted on offline servers. If you want to post images in your post, please use the attachment tool - the # button in the advanced editor toolbar - to upload images to the forum and attach thumbnails to your post.

I've reduced the huge image in your post above to a clickable link and merged two consecutive posts.

---

### Post by Dennis N on 2016-11-06
> * how about the showing only the non-minimised windows like how macos does it? (on the askubuntu links)

 Yes, in XFCE as an option you can exclude "iconified" (minimized) windows from showing in the alt-tab switcher (either mode).

---

### Post by CantankRus on 2016-11-06
How does Windows task viewer differ from the way I showed you to set up Scale?
Forums not allowing me to attach posts so have a look at below imgur links.
[http://imgur.com/sxtWBFz](http://imgur.com/sxtWBFz)
[http://imgur.com/a/gLMRv](http://imgur.com/a/gLMRv)

---

### Post by linuxhard on 2016-11-06
* gonna look into kde maybe other options, but xcfe 
** with basic stuff like 1) window titles, 2) minimised window not showing, looks like the best bet right now
*** pic previews arent super needed
**** if something can show the favicon of the website instead of the chrome icon, that would be AMAZINGLY HUGE

* task view is to show how the alt tab basically looks like
* compiz + scale, the text should be easy to see & read which it isnt and the positioning in the center isn't a good idea
** but the pics are large and fit to the fullscreen and that's good

--

* i looked into tiling windows, those arent good for chrome windows 

chromebooks have a dedicated window switcher (that's how important it is)

small pic of the switcher -- [https://9to5google.files.wordpress.com/2016/10/chrome-os-54-stable-switch.png?w=1000&h=305](https://9to5google.files.wordpress.com/2016/10/chrome-os-54-stable-switch.png?w=1000&h=305)

---

### Post by CantankRus on 2016-11-06
> **linuxhard said:**
> * compiz + scale, the text should be easy to see & read which it isnt and the positioning in the center isn't a good idea
Then make it easier to see.

---

### Post by linuxhard on 2016-12-07
* can gnome (with anything like compiz) -- show only windows that are not minimised?
** like in [https://ubuntuforums.org/showthread.php?t=2342305&p=13566719#post13566719](https://ubuntuforums.org/showthread.php?t=2342305&p=13566719#post13566719)

i have a different solution now,

can gnome + compiz

show the titles of all the chrome windows on the 'taskbar' (w/e location you have it in) ??

why wasn't [https://extensions.gnome.org/extension/15/alternatetab/](https://extensions.gnome.org/extension/15/alternatetab/) 

recommended? 

that seems to solve almost all the problems that this thread had presented, no?

---

