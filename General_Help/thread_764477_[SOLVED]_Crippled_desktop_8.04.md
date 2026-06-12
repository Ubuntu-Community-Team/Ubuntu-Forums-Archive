---
title: "[SOLVED] Crippled desktop 8.04"
date: 2008-04-23
forum: General Help
---

### Post by c1rcu17 on 2008-04-23
Ok, a picture really is worth a thousand words, so here is on of my problem,
[http://img229.imageshack.us/my.php?image=helpwj7.png](http://img229.imageshack.us/my.php?image=helpwj7.png)

basically, i upgraded to 8.04, and my menu bar is totally gone, not to mention there is a strange purple border around the windows, menus, and mouseover tooltips. I think it has to do with compiz. I have acess to a terminal, and nothing else. Help Please!

---

### Post by tamoneya on 2008-04-23
What happens when you run:
```
gnome-panel
```

---

### Post by tamoneya on 2008-04-23
age has nothing to do with it and linux is not necessarily harder or easier than windows.  They are different.  I think what you are trying to get at is the fact that people who have been using windows for more years than you have will run into trouble if they try to transition.  But I am also certain that there are many people much older than you who can use linux much better than you can.

---

### Post by justin whitaker on 2008-04-23
<snip>
I'm 36, and I run Linux. Age has nothing to do with it. All it takes is a free mind and a willingness to learn. I think you need to rethink your statements, and whether your attitude helps the cause.

---

### Post by mrfraser89 on 2008-04-23
<snip>

People come on here to get help so they can learn to use the OS.

I doubt the first time you installed and used Ubuntu or any other Linux distro you knew exactly what you were doing all the time and had no troubles.

Negative attitudes like this deter people from asking questions and from trying new things (eg Linux?)

You were helpful though, I'll give you that..

---

### Post by justin whitaker on 2008-04-23
> **c1rcu17 said:**
> Ok, a picture really is worth a thousand words, so here is on of my problem,
[http://img229.imageshack.us/my.php?image=helpwj7.png](http://img229.imageshack.us/my.php?image=helpwj7.png)

basically, i upgraded to 8.04, and my menu bar is totally gone, not to mention there is a strange purple border around the windows, menus, and mouseover tooltips. I think it has to do with compiz. I have acess to a terminal, and nothing else. Help Please!

You can remove compiz via the terminal...HOWEVER, you might hose GNOME. 

[http://ubuntuforums.org/showthread.php?t=690582](http://ubuntuforums.org/showthread.php?t=690582)

It depends on your system and video card, apparently. 

With that warning, here is how you do it:

[http://www.ubuntugeek.com/howto-remove-compiz-fusion-including-config-files.html](http://www.ubuntugeek.com/howto-remove-compiz-fusion-including-config-files.html)

What I would do, first, is apt-get install some minimal WM, so you have something to drop back into if you hose gnome by accident.

---

### Post by ibuclaw on 2008-04-24
<snip>

Typical Teenager... Thinks the world isn't as smart as him...
I pity you.

In other news.
Hit **Alt+F2** and type in:
```
metacity --replace
```
Then hit **Alt+F2** again. Then:
```
killall gnome-panel
```

That should hopefully do it.

To keep metacity as your window manager.
**Alt-F2**, Type in:
```
gconf-editor
```
And go into
"**/desktop/applications/window_manager**" in the registry.
And change the values of "**current**" and "**default**" from "**/usr/bin/compiz**" to:
```
/usr/bin/metacity
```
Close the app, logout, login.

Regards
Iain

---

### Post by angry_johnnie on 2008-04-24
I'm not sure whether Alt+F2 will work without gnome-panel, but I think it doesn't... Anyway, you could still do what tinivole suggested from a terminal, since you've already got a launcher for it on the desktop.

killall gnome-panel   would be the first thing to try.

If that doesn't do it, you could do this:

```
metacity --replace & disown
```

then you can try again

```
killall gnome-panel
```

Just in case it's already running, but not being displayed.

If it doesn't show up, you could try

```
gnome-panel & disown
```

If you want to, you could go back to compiz, and, with some luck, the panel will still be there.  If not, you can always go back to metacity :-)

If you decide to remove compiz, do it with **apt-get remove**, or via Synaptic.  Removing directories is not the way to go :-)

Good luck!

---

### Post by c1rcu17 on 2008-04-24
So i think I'm on to something. You guys were right. somehow gnome-panel decided to remove itself. I used apt-get to get it back, but when gnome-panel starts up, some of the applets are gone. See the image for the errors I get.

[http://img98.imageshack.us/img98/8107/gnomepanelkw9.png](http://img98.imageshack.us/img98/8107/gnomepanelkw9.png)

any ideas on how to get those back?

Also, now that compiz drop shadow is not purple anymore, it is yellow.
Thanks for your help guys!

P.S.

I'm 20 and have been using Ubuntu for about 9 months. I am normally able to fix my problems myself. I just have never run into this before.

---

### Post by unbuntued on 2008-04-24
Hey folks,

I just upgraded to Hardy and am facing a similar problem.
In my case, I don't see the desktop bar or anything else (gnome-panel basically). But some applications still load on start-up.

I logged in in terminal mode, and tried the following without any successful result:
- Removed gnome-panel, reboot and reinstall it
- Removed compiz (through sudo apt-get remove compiz)

I'm still stuck with the problem. Any suggestions?

Update: booting with GNOME gets a bunch of error window that flicker then disappear. Nothing afterwards.

---

### Post by bapoumba on 2008-04-25
Removed two posts and snipped the quotes in remaining posts :)

---

### Post by c1rcu17 on 2008-04-25
You may have to try reinstalling gnome-applets. That and gnome-panel reinstall did the trick for me. 

Anybody have any ideas on the purple fuzz window borders? It has to do with compiz drop shadows and Nvidia's drivers. I have an 8600GT card. I still don't know how to fix it.

---

