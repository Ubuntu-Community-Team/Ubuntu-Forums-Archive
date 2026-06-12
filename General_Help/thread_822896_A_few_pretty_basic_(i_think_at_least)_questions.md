---
title: "A few pretty basic (i think at least) questions"
date: 2008-06-08
forum: General Help
---

### Post by edstittle on 2008-06-08
Hey,

I've just replaced my vista installation with Ubuntu and have been pretty please so far. Just ran into a few problems that I have no idea how to fix and it doesn't help I dunno the proper terms for it so I'm not sure what keywords to use when searching for it. I know I'm not listing any stats about my installation but it's pretty simple... I've just downloaded the latest file from the Ubuntu website and haven't modified or updated anything else.

1) The "tray" where all my applications are minimized to appears to have dissapeared, how'd I get it back?

2) I've also accidentally deleted my wireless network connecting button on the toolbar. I know you can access it though administration >> network but I liked how simple the other was. How'd I get it back (again) lol?

3) Am I running GNOME? As I said all I've downloaded is the Ubuntu main file off the website but I keep seeing refrences to GNOME so I assume I'm running it?

4) Finally can anyone reccomend me any programmes worth downloading, I've looked around but since I'm a complete noob to this I might be missing some basic ones? Is WINE worth downloading?

Thanks for your help guys, hopefully they're all pretty simple questions.

---

### Post by Tom--d on 2008-06-08
1. Right click the panel and go to Add to panel > then look for notification area.

2. I think you are referring the nm-applet. Press ALT + F2 and type in nm-applet.
If that is what you are talking about. Go to System > Pref > Sessions > Network Manager should be there, tick it. If its not there, go to add and then call it Network manager and the command to 
```
nm-applet
```
And enable it. This will make it run at start up.

3. Yes you are running GNOME. 
Go to System > Admin > System Monitor > System and it tells you about your computer.

4. Look in Add/remove (Applications > Add/remove)
Look around. there are many things you can install.

Wine is worth downloading if you want to run a windows program. But beware that it might now work tho.

Anything else, just ask :)

---

### Post by edstittle on 2008-06-08
Thanks for that speedy response. The nm-applet apparently should already show (but it doesnt) however when I added the notification area that added the network button too as well as the bar that shows some applications that you're running (like it has a little icon showing my Pidgin status).

But what I meant was like the entire bar when I minimize my applications like firefox and pidgin they're displayed in rectangles along the bottom of the screen just like they are in WINDOWS and then you can click them so they resume maximized...

[http://img338.imageshack.us/img338/4535/th25053bb.gif](http://img338.imageshack.us/img338/4535/th25053bb.gif)

^^ that, but obviously the Ubuntu version of it. I swear when I first installed it I had one but I was playing around customizing things and now I just can't find it.

Thanks again :D.

---

### Post by Tom--d on 2008-06-08
O right, I see ;)

Thats an easy one.

Right click the panel again, add to panel.

Then go to Window List and double click it.. and move it around etc etc :)

---

### Post by Tom--d on 2008-06-08
Also, when you have been helped.

To be nice, you can click the star next to edit, quote on the peoples posts. 
It says thanks to that person :)

---

### Post by Tomatz on 2008-06-08
**Rclick on the bar/panel** at the bottom of your screen, click **"add to panel"**, select **window list**.

Done :)

---

### Post by edstittle on 2008-06-08
Wow, again that was very simple. Thanks to the both of you and I've made sure to star all your posts :).

---

### Post by yman on 2008-06-11
Try System -> About GNOME for information about GNOME. GNOME is what is called a Desktop Environment, and among many things it includes:
[LIST]
[*]Metacity - Window Manager.
[*]GDM - GNOME Display Manager. This is the program for logging in to the desktop.
[*]GTK+ - Graphical Toolkit Library.
[/LIST]
As well as the desktop, with it's wallpaper and panels.

If you got all the answers to your questions, mark the thread as [SOLVED] by opening the "Thread Tools" menu and selecting "Mark Thread as Solved". The "Thread Tools" menu appears close to the top of the page.

---

### Post by Pjotr123 on 2008-06-11
This is a handy to-do list after a fresh installation:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)

---

### Post by Uchiha_madara on 2008-06-11
Ok ....SomeBody tell Me What is Wubi??????????

---

### Post by Pjotr123 on 2008-06-11
> **Uchiha_madara said:**
> Ok ....SomeBody tell Me What is Wubi??????????

A way of installing Ubuntu *within* Windows. Nice and easy, but a "normal" installation is better and only slightly more difficult:
[http://ubuntutip.googlepages.com/installationofubuntu](http://ubuntutip.googlepages.com/installationofubuntu)

Greeting, Pjotr.

---

### Post by DavidAndrew2008 on 2008-06-11
> **edstittle said:**
> 4) Finally can anyone reccomend me any programmes worth downloading, I've looked around but since I'm a complete noob to this I might be missing some basic ones? Is WINE worth downloading?

Thanks for your help guys, hopefully they're all pretty simple questions.
WINE is worth downloading as it won't take up much HD space so you've nothing to lose, but in my experience the compatibility rate isn't that good. Basically, if you have a lot of Windows programs/games that you intend to use regulary then you are better off sticking to running them from the real thing. There are others programs such as Cedega that do a better job of emulating Direct X games, but again, (in my experience) the compatibility rate is below average, and for those games that do work you'd be lucky to get a decent performance.

As for linux programs, the "Add/Remove" applications from your desktop browser is the best way to determine what games and programs are available for your system. It also has a user rating to determine how popular the software is. There is also this website for downloading software:

[http://linux.softpedia.com/]("http://linux.softpedia.com/")

Scroll down to the bottom and on the right hand side you'll see the categories in the blue box. I recommend you only download the "deb" packages as they install your software automatically. All of the other types of files need to be compiled, which can be a bit of a ballache.:mad:

---

### Post by yman on 2008-06-13
> **Uchiha_madara said:**
> Ok ....SomeBody tell Me What is Wubi??????????

It installs Ubuntu as a file inside widows, and allows you to uninstall it like any other Windows program. The upside is you don't need to deal with partitioning. The downside is worse performance than in a regular install. You can also turn a Wubi installation into a normal one, or so I've heard.

[http://wubi-installer.org/](http://wubi-installer.org/)

EDIT: Oops. I didn't notice this question was already answered. Sorry.

> There is also this website for downloading software:

[http://linux.softpedia.com/](http://linux.softpedia.com/)

But then you won't get automatic updates.

---

