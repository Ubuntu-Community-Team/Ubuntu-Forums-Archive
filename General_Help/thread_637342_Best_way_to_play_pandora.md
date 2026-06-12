---
title: "Best way to play pandora?"
date: 2007-12-10
forum: General Help
---

### Post by vav on 2007-12-10
Amarok doesnt have a plugin for it :( Firefox doesnt have an extension that supports it fully :((

What's the best way to play Pandora in gutsy giving it a most music player like experience? I'm a little tired of running it through a browser window!

I was thinking along the lines of a screenlet/gnome-dock applet/taskbar applet/no-border browser that displays HTML/Flash and can handle cookies/whatever login authentication pandora uses... and also the flash rating of songs, creation of stations etc... i.e. full functionality without appearing like a browser :P

Ideas please?! Thanks!

---

### Post by hollaburoo on 2007-12-10
I've tried doing the same thing, and as far as I know there is NOTHING out there for linux.
Its horrible.

---

### Post by Lostincyberspace on 2007-12-10
I have only been able to do it online. Last FM is pretty good but not as good as Pandora in my opinion.

---

### Post by vav on 2007-12-11
I guess the better question to ask is:
Is there a standalone player for gutsy (I tried gnash and it doesnt work for this) that can play flash off websites?

---

### Post by vav on 2007-12-11
Here is the best I found so far:

HOW TO:
Use galeon in minimal mode with launcher to play pandora

Steps:
1> Login to pandora and access your account and start playing radio (firefox)
2> Go to View->Page Source and search for swf. Eventually you'll find an entry saying [https://....tuner_1_2_3_4_pandora.swf](https://....tuner_1_2_3_4_pandora.swf) where 1 2 3 4 will be some 4 digits. Copy this link
3> Copy and paste this link into the firefox window. It will redirect to a simpler link very much like the first one. Copy this simpler link.
4> Install galeon through synaptic
5> Create a launcher with command 'galeon [http://...simplerlink](http://...simplerlink)...'
6> The first time galeon starts, go to the view menu and disable the toolbar, sidebar etc... all that you can. Finally you should only have one menu bar and then pandora. Resize the window to what you want to see of pandora. Close galeon
7> Give an icon to the launcher... this could be from firefox's cache of the address bar pandora icon.

Launch Pandora as a standalone app! well nearly. Now the main browser is also free to do other stuff!

One question remains: can galeon be started without the menu bar? from the command line? Can the title be controlled from the command line too? If so we could really have a pandora player :)

---

### Post by Islington on 2007-12-24
sorry to revive such an old thread, but I have been playing pandora in Songbird, in a separate tab.


its amazing...

---

### Post by jaspen.p on 2008-05-22
Thanks for the walk through vav.
Galeon works fairly well. I made my own launcher as suggested and then created a new icon for it. I attached it here if any one else want to use it.

To copy it into the folder with the other icons in terminal type
sudo cp /...file location../Pandora.png /usr/share/pixmaps/Pandora.png

To set the icon
[LIST]
[*]right click on the launcher
[LIST]
 properties
[/LIST]
[*]click on the icon image
[*]select Pandora.png
[*]ok
[/LIST]

---

### Post by jaspen.p on 2008-05-22
I was playing around with how to change the explore window icon and found that if you save the Pandora.png as gadeon.png as explained above the gadeon explorer window will use that as its' icon at the top and in the task bar. 

Make sure you save a copy of the original gadeon.png before overwriting it if you want to change it back in the future. 
 
I think this is about as close as you can get to a custom app without changing any of the source code for the browser to remove the toolbar.

---

### Post by kerry_s on 2008-05-22
you guys know about the mini command?

[http://www.pandora.com/?cmd=mini](http://www.pandora.com/?cmd=mini)

there's also a bookmarklet around.
found 1-> [http://pmhesse.blogspot.com/2006/09/pandora-bookmarklet.html](http://pmhesse.blogspot.com/2006/09/pandora-bookmarklet.html)

this is what the bookmarklet does->

---

### Post by edandersen86 on 2008-07-03
If you go to [http://pandora.com/desktop](http://pandora.com/desktop) there is an Adobe AIR pandora client. I have not tried this on linux yet, but AIR is supposed to be linux compatible, so it's worth a shot.

---

### Post by thiebaude on 2008-07-03
That link doesn't support linux, only windows and mac

---

### Post by webmaren on 2008-07-08
[http://labs.adobe.com/downloads/air_linux.html](http://labs.adobe.com/downloads/air_linux.html)

There's the link to the Linux Alpha for Adobe Air.

Only problem is I can't actually install the program.

```
$ sh '~/Desktop/adobeair_linux_a1_033108.bin'
~/Desktop/adobeair_linux_a1_033108.bin: 1: Syntax error: "(" unexpected
```

---

