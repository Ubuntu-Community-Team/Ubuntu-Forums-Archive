---
title: "Lubuntu &amp; Docky transparent not working?"
date: 2013-07-10
forum: General Help
---

### Post by WarrenSH on 2013-07-10
Running the latest verison of Lubuntu 32bit & Docky. I installed CompizConfig Settings Manager 

"sudo apt-get install compiz" & "sudo apt-get install compiz compizconfig-settings-manager compiz-plugins"

But I still can't get Docky to be transparent...

How can I fix this any ideas?


[IMG]http://s23.postimg.org/v6ivuszmj/2013_07_10_190237_1280x800_scrot.png[/IMG]

---

### Post by SantaFe on 2013-07-10
I know it's not Compiz, but I found this :[http://www.lubuntutips.com/2011/12/lubuntu-composite-manage-xcompmgr.html](http://www.lubuntutips.com/2011/12/lubuntu-composite-manage-xcompmgr.html)

Tried it in Lubuntu with both Docky & Cairo-Dock (I know, it's supposed to be called GTX-Dock, but I'm weird) and following instructions, it worked fine. ;)  I also found this page:[http://crunchbang.org/forums/viewtopic.php?id=4231](http://crunchbang.org/forums/viewtopic.php?id=4231) with some xcompmgr flags, but so far the default settings work fine for me.

Hope this helps.  BTW: xcompmgr can be found in the Synaptic Package Manager, as well in the Lubuntu Software Center if you don't want to use the apt-get method shown in the first link. ;)

---

### Post by claracc on 2013-07-11
I do not use compiz but metacity, but I think you will have to enable compositing in compiz.

Using the compizconfig-settings-manager, you will have to click on "Enable OpenGL", then a window will open that says "OpenGL requires the plugin Composite", click on "Enable Composite".

---

### Post by WarrenSH on 2013-07-11
I did sudo apt-get install xcompmgr

& it installed but i'm confused on how to do this 

> [COLOR=#000000][FONT=Arial]Enter your password and you're done. [/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]However, installing xcompmgr is useless unless you set it to autostart at login. This part is a bit trickier. The simple method is to download the following .desktop file[/FONT][/COLOR][xcompmgr.desktop]("http://dl.dropbox.com/u/35272968/Blog/xcompmgr.desktop")[COLOR=#000000][FONT=Arial]and place it in the directory:
[/FONT][/COLOR][COLOR=#000000][FONT=Courier New]**~/.config/autostart**[/FONT][/COLOR]

where is this directory at? I can't find it :confused: please explain this to me step by step. 

thanks ;) 

Also I followed this tutorial [http://www.lubuntutips.com/2011/12/lubuntu-composite-manage-xcompmgr.html#.Ud5QCY7q6PD](http://www.lubuntutips.com/2011/12/lubuntu-composite-manage-xcompmgr.html#.Ud5QCY7q6PD)

---

### Post by WarrenSH on 2013-07-11
BUMP BUMP 

Still still need help with the above reply

---

### Post by SantaFe on 2013-07-11
the .config folder is in your home directory, but it's a hidden file.  To see it, in Thunar or PCManFM press CTRL+H to show the hidden files.  Then click on .config, then the autostart folder & drag the desktop file into it.  See snapshots below.  The first one is after running Thunar & pressing CTRL+H, it shows the .config folder.  The second one is after opening the .config folder showing the autostart folder.  And the third is the opened autostart folder, with the xcompmgr.desktop file in place. ;)

---

### Post by WarrenSH on 2013-07-11
Thanks this worked out very well for me. Now my final issue is adding the Terminal & Transmission to the dock how is this possible? 




> **SantaFe said:**
> the .config folder is in your home directory, but it's a hidden file.  To see it, in Thunar or PCManFM press CTRL+H to show the hidden files.  Then click on .config, then the autostart folder & drag the desktop file into it.  See snapshots below.  The first one is after running Thunar & pressing CTRL+H, it shows the .config folder.  The second one is after opening the .config folder showing the autostart folder.  And the third is the opened autostart folder, with the xcompmgr.desktop file in place. ;)

---

### Post by SantaFe on 2013-07-11
It's easier in Xubuntu, where you can find the application in the menu, then click on it & drag it to the Docky bar.  In Lubuntu, that doesn't work.  A little trick I found, is to create a folder in your home folder, I call mine DockyShortcuts, then right click on the program entry in the menu & pick Add To Desktop.  Then drag that icon to the folder you created, THEN drag that copy to the Docky Bar.  You can then delete the Desktop Icon if you want

I tried just dragging the desktop icon to there, and it worked until I decided to get rid of the desktop icon, then the Docky one quit working. ;)

Have no idea why it has to be different in Lubuntu, would rather it was like in Xubuntu myself as it's only one step instead of 3. ;)

---

### Post by WarrenSH on 2013-07-12
I did what you said & I'm not able to drag & drop from shortcut folder to the dock. It's not accepting the apps for some reason hm... The main reason i'm using Lubuntu is because my laptop is 8 years old and needs a light weight distro. any other ideas for a light weight distro? I was using xubuntu but it was a bit sluggish vs Lubuntu is super fast. 

> **SantaFe said:**
> It's easier in Xubuntu, where you can find the application in the menu, then click on it & drag it to the Docky bar.  In Lubuntu, that doesn't work.  A little trick I found, is to create a folder in your home folder, I call mine DockyShortcuts, then right click on the program entry in the menu & pick Add To Desktop.  Then drag that icon to the folder you created, THEN drag that copy to the Docky Bar.  You can then delete the Desktop Icon if you want

I tried just dragging the desktop icon to there, and it worked until I decided to get rid of the desktop icon, then the Docky one quit working. ;)

Have no idea why it has to be different in Lubuntu, would rather it was like in Xubuntu myself as it's only one step instead of 3. ;)

---

### Post by SantaFe on 2013-07-12
That's weird.  However I did find this, which I didn't know about: 
> 
For anyone new to using docky in lubuntu just thought i would share something i found out.

To add a app icon to docky you need to open the app and then right click on the apps icon that appears in docky then click "pin to dock" so for example open "lx terminal" from acessories  a icon for lx terminal will appear in docky now right click the icon and click "pin to dock".  Job done :) :)


Maybe you might give that a try? ;)

---

### Post by WarrenSH on 2013-07-12
didn't work :( 

> **SantaFe said:**
> That's weird.  However I did find this, which I didn't know about: 


Maybe you might give that a try? ;)

---

### Post by WarrenSH on 2013-07-12
I left Lubuntu for elementary OS

[IMG]http://i42.tinypic.com/2mdnlma.png[/IMG]

---

### Post by edb66083 on 2013-07-12
> Thanks this worked out very well for me. Now my final issue is adding the Terminal & Transmission to the dock how is this possible? 

To add items to Docky, the easiest way is to just start the application normally from the menu. The app will show up in docky. Right click on the app, and select 'Pin to Dock'. This will make it permanent (you can always delete it from docky later, of course).

---

