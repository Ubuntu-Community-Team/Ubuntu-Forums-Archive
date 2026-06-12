---
title: "problem .. GNOME-Do integration via plugin with Zim 0.60 Desktop Wiki"
date: 2013-08-26
forum: General Help
---

### Post by dragonfly41 on 2013-08-26
I've followed this helpful starter tutorial on use of Zim Desktop Wiki.

[http://www.youtube.com/watch?v=yBZpWgzO9Ps](http://www.youtube.com/watch?v=yBZpWgzO9Ps)

I've installed Zim version 0.60 on Ubuntu 12.04.

I was interested in use of GNOME-Do as seen in the above tutorial (towards the end of clip) so I installed GNOME-Do through Ubuntu Software Centre.

Then launching GNOME-Do > Preferences > Plugins > All Plugins

to enable Zim plugin to access Zim pages.

The "Configure" buttom for some plugins (including Zim plugin) seems to be disabled (grayed out) so I can't configure any plugin settings.
There are a few plugin options where "Configure" is seen to be alive - e.g. "Files and Folders", "Pastebin".

Nor does clicking "About" button help for any plugin.  This link directs to a dead domain .. [http://do.davebsd.com/](http://do.davebsd.com/)


I've found that the GNOME-Do configuration files are in ~/.gconf/apps/gnome-do/preferences/Do

but I don't see where I can tweak Zim plugin to find Zim.

And there isn't much to be seen here ..

[http://www.mail-archive.com/search?q=gnome-do&l=zim-wiki%40lists.launchpad.net](http://www.mail-archive.com/search?q=gnome-do&l=zim-wiki%40lists.launchpad.net)

...

So to summarise the symptoms are ..


[LIST]
[*]I launch GNOME-Do from Applications > Accessories
[*]I type "zim"
[*]Zim is recognised and the Zim icon appears in GNOME-Do popup
[*]but Zim does not launch/run beyond that point ... as shown in this tutorial ... towards the end ...
[/LIST]

        [http://www.youtube.com/watch?v=yBZpWgzO9Ps](http://www.youtube.com/watch?v=yBZpWgzO9Ps)


Any tips to get GNOME-Do and Zim to work together?

---

### Post by tgalati4 on 2013-08-27
What comes up when you hit Alt-F2?

What happens when you open a terminal and type in *zim*?

I'm running zim 0.56 on Linux Mint Mate 14 (based on 12.10).  Perhaps there is an issue with version 0.6 on 12.04.

What is the output of:

```
apt-cache policy zim
```

It might look something like:

tgalati4@Mint14-Extensa ~ $ apt-cache policy zim
zim:
  Installed: 0.56-1
  Candidate: 0.56-1
  Version table:
 *** 0.56-1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/universe amd64 Packages
        100 /var/lib/dpkg/status

---

### Post by stinkeye on 2013-08-27
Don't use gnome-do or Zim but maybe for the Zim functionality you need to install
the **gnome-do-plugins** package.

I do use kupfer which is similar to gnome-do without the [**_[COLOR="#B22222"]mono[/COLOR]_**]("http://www.mono-project.com/What_is_Mono") reliance.
kupfer also has a Zim plugin.

---

### Post by dragonfly41 on 2013-08-27
**[tgalati4]**

I should have clarified that Zim desktop wiki launches and runs from either the menu or launcher or terminal. It is in regular use.

The problem is managing Zim via GNOME-Do zim plugin .. which does not launch Zim.

Here is my output from command: apt-cache policy zim

[COLOR=#0000ff]$ apt-cache policy zim
zim:
  Installed: 0.60
  Candidate: 0.60
  Version table:
 *** 0.60 0
        100 /var/lib/dpkg/status
     0.60~precise1 0
        500 [http://ppa.launchpad.net/jaap.karssenberg/zim/ubuntu/](http://ppa.launchpad.net/jaap.karssenberg/zim/ubuntu/) precise/main i386 Packages
     0.54-1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise/universe i386 Packages[/COLOR]

[B]
[stinkeye][/B]

I have previously installed gnome-do-plugins

[COLOR=#0000ff]sudo apt-get update
sudo apt-get install gnome-do-plugins[/COLOR]

I tried your suggestion to install Kupfer (keeping GNOME-Do installed as alternative).

I enabled zim plugin in Kupfer preferences.

I typed "zim" to bring up the Zim launch icon.

but I still can't launch Zim via Kupfer or communicate between Kupfer and Zim .. same problem as when using GNOME-Do.

Meanwhile Zim can be launched directly from menu or launcher button.   It is in regular use.   Just cannot be managed via GNOME-Do or Kupfer.

---

### Post by stinkeye on 2013-08-27
???? No idea.
I installed zim and it launches with kupfer.
Plugin seems to work.

First run brought up this window...
[ATTACH=CONFIG]245756[/ATTACH]

Then I made a couple of test pages in zim, restarted kupfer
and I could then search zim pages.
Not being able to launch zim at all is strange though as I thought that would work with any application
that installs a .desktop file to /usr/share/applications.

---

### Post by dragonfly41 on 2013-08-27
Thanks for trying Zim with Kupfer.

I checked ownership of /usr/share/zim .. and I saw that it was root:root.

So I tried changing ownership to user:user

I can now launch Zim from Kupfer by double clicking on Launch icon in Kupfer.

but there is still no access to Zim API through Kupfer (or GNOME-Do).


These desktop files are present ...
[COLOR=#0000ff]/usr/share/applications/kupfer.desktop
/usr/share/applications/kupfer-exec.desktop
/usr/share/applications/gnome-do.desktop[/COLOR]

---

### Post by stinkeye on 2013-08-27
Files should be owned by root. Don't think thats the problem.

So if you start kupfer, type in "zim" and press enter when the right tile shows launch (pic), zim won't start.
The right tile shows the action to be performed. Hit TAB then down arrow to change the action.

...but you can launch zim by searching in the dash?
May seem obvious, but just checking.

---

### Post by dragonfly41 on 2013-08-27
I've restored Zim permissions to root.

I must admit it was not obvious to me that I needed to tab between the two buttons and hit down arrow.

I did try that tab-downarrow key sequence and a menu appears and I can launch Zim.

But I don't see any extra features such as searching or navigating to a specific Zim notebook page and so the advantage of using Kupfer or GNOME-Do is lost on me.

I also tried tab-downarrow key sequence in GNOME-Do and that works.  So that key sequence was the missing link.

I think I'll have to quietly drop the idea of using GNOME-Do or Kupfer in my workflow but thanks for persevering.
I can continue using Zim as an application launched from menu.

---

### Post by stinkeye on 2013-08-27
Ok no problem.
The zim plugin needs to be enabled in kupfer preferences.
With kupfer open click on the text "kupfer" RHS of window.

Try again after a reboot if inclined.
The zim plugin didn't work for me straight away.
I rebooted and it started to work.
Goodluck.

---

### Post by dragonfly41 on 2013-08-27
Tried again after rebooting ..

Launched Kupfer from Applications > Accessories > Kupfer

Kupfer launcher is now seen in Ubuntu top right toolbar

after typing "zim" in Kupfer Main Interface .. and then <tab>+<down_arrow> key sequence 

a drop down menu appears with initially three options ...

Launch
Search Contents
Add to Favorites

Launch works and as expected launches Zim

If I choose "Search Contents" I get "zim Pages is empty".

I can use "Add to Favorites" .. and then "Remove from Favorites" .. so the plugin works.
 
What features am I missing in Kupfer to get more out of Zim?   
Still not too clear what benefits in workflow I might get if I get the two to work together.

Thanks for advice so far.

---

### Post by stinkeye on 2013-08-27
Yeah you'll just have to play around with it to see if it's useful.
I was going to link to the kupfer help wiki but it seems to be down.
If I enter zim in kupfer and then press the down arrow it shows zim with an arrow symbol to the right...
[ATTACH=CONFIG]245782[/ATTACH]

Then hitting the keyboard right arrow shows my zim pages...
[ATTACH=CONFIG]245783[/ATTACH]

I can also search for a zim page by typing the name of a page.
If the kupfer window isn't showing a zim page hit the down arrow to show more matches.
**NOTE if you delay too long between keystrokes, kupfer starts a fresh search.

To be honest I mainly use kupfer as a launcher and don't use many of
the plugins as I find them awkward or hard to understand.
Using the plugins takes a bit of learning and have found some to be good once you get a rhythm going.

The benefit I see in kupfer is its a fast uniform launcher that I can use
across my different installed desktop sessions.

---

### Post by tgalati4 on 2013-08-28
Don't forget, zim has a panel icon that you can activate in zim's preferences==>plug-ins==>tray icon.  I find it useful.  I rarely start zim because I have it running all the time in its own workspace.

---

