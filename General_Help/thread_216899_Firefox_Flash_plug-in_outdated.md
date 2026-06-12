---
title: "Firefox Flash plug-in outdated"
date: 2006-07-16
forum: General Help
---

### Post by Luke771 on 2006-07-16
I often get messages like "you need a newer Flash plugin to see this animation" (... to play this game etc)
But when I hit "install" I get redirected to the same plugin I already have, which is the latest available for Linux (flash-plugin-7).

Is there any Flash 8 for Linux?
Or any other plugin that plays *all* flash stuff?
Where do I get it?
How to install?

---

### Post by MakubeX on 2006-07-16
here's my setup:

[http://nightfox.wordpress.com/2006/06/25/flash-player-85-on-linux/](http://nightfox.wordpress.com/2006/06/25/flash-player-85-on-linux/)

---

### Post by Luke771 on 2006-07-16
Awsome. Works perfectly.
Thanks.

Is there a way to make it work in the regular Linux Firefox?
Do I need to wine the Windows version each time I want to play a Flash?

---

### Post by Ramses de Norre on 2006-07-16
There is no native flash 8 for Linux and there never will be one, but macromedia will release flash 9 for windows and Linux at the same time. I guess we'll have to wait untill then for full flash support.

---

### Post by HAARP on 2006-07-16
Actually, Flash9 has already been released. No Linux version.
I wish there was a way to fool sites into thinking you're using 8/9. Most Flash content works fine with 7.

---

### Post by Ramses de Norre on 2006-07-16
Really? I thought they planned to release both at the same time.. well I hope flash 9 will be available anytime soon then..

---

### Post by yopnono on 2006-07-16
> **Ramses de Norre said:**
> Really? I thought they planned to release both at the same time.. well I hope flash 9 will be available anytime soon then..

Humm... I think, you and I have to wait.
[http://weblogs.macromedia.com/emmy/](http://weblogs.macromedia.com/emmy/)

```
Q. Wasn't there supposed to be a simultaneous release of the Linux version of Flash Player 9?
A. Not exactly. We never said it would sim ship. 
We did say that we were skipping the v8 port to get a start on porting v9 (formerly known as v8.5). 
We are working on it, and expect to release in early 2007. 
Which means a beta should be here very soon. 
For progress and updates, check Mike's Penguin.SWF blog.
```

---

### Post by Luke771 on 2006-07-16
Yes most flash stuff will work with 7... but not *all* of it. So I added a custom panel launcher that runs the line ```
wine /<path/to/windows-partition/firefox>/firefox.exe
```I didn't actually need to use the trick suggested above because I'm on a dual boot system with Windows (= I already have an installed firefox.exe) but I used the same "trick".
I'll keep running the "regular" Linux-Firefox with Flash7 and switch to wine-windows-firefox when I want to play some Flash that won't run on 7.
Not that it happens all the time, but it feels good to know that I *can* play even those flash that require version 8 without having to switch OS

BTW when will it become possible to wine MS Flight Sim?
That's like the *only* reason why I'm not on 100% Linux yet.
(and don't talk about X-Plane: it sucks)

OK this is not the right place to start a FS vs. X-P discussion, but maybe I'll start a thread about trying to wine FS9 in the games forum.
Or maybe someone else will (I'm kinda lazy...)

---

### Post by roostishaw on 2006-07-17
> **MakubeX said:**
> here's my setup:

[http://nightfox.wordpress.com/2006/06/25/flash-player-85-on-linux/](http://nightfox.wordpress.com/2006/06/25/flash-player-85-on-linux/)

That howto doesn't give you flash 9. Just go to [www.getfirefox.com](www.getfirefox.com) and install the latest windows version it with wine. Then run:
```
wine .wine/drive_c/Program\ Files/Mozilla\ Firefox/firefox.exe
```
Then just go to google video or somewhere and click 'install missing plugins' when Firefox prompts you to. Then you'll have flash 9. To check that it worked go to about: plugins (without the space after the colin).

---

### Post by JerMe on 2006-07-18
... and once you have Firefox installed under Wine, make a desktop "shortcut" for your Wine-Firefox to make life even easier.  Right click your desktop, choose "Create Launcher...", add a name for your shorcut in the Name field, and enter "wine .wine/drive_c/Program\ Files/Mozilla\ Firefox/firefox.exe" as the command.  Make sure you select "Application" in the drop down box as the Type.

The next time you run into those pesky Flash 8/9 websites, just use your Wine-Firefox shortcut. :cool:

---

### Post by Bokonon on 2006-07-18
If you have wine running, you can also install IE with flash pretty easily by going to the following site.  [ie4linux]("http://www.tatanka.com.br/ies4linux/news/")

I prefer firefox to ie, but for some sites you need ie for full functionalilty.

---

