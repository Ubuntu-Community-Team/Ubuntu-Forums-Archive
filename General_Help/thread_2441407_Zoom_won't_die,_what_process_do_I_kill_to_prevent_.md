---
title: "Zoom won't die, what process do I kill to prevent respawning?"
date: 2020-04-23
forum: General Help
---

### Post by goemonburo on 2020-04-23
I've gotten Zoom up and running on my Lubuntu system, but every time the screensaver comes on (or rather, every time I re-login after it's locked the screen) there's a "Join Zoom Meeting" window there.  No matter what I do.  

I've killed it multiple times by "ps aux"ing and killing the offending PID.  But what process is causing it to be there in the background?  I don't want to uninstall (it was a bit more work to get it running to begin with!) and I really just want to know that when I've stopped Zoom, it's really stopped.  (Especially with all the privacy issues.)

Anyone else have this issue?  Does anyone know how to solve it?

Thank you so much for any and all help you can offer!!

---

### Post by SeijiSensei on 2020-04-24
Usually when I kill the main Zoom window(s), the process continues to run with an icon in my task bar.  (I'm on KDE, though I'd imagine the same is true for other flavors of Ubuntu.)  I can right-click the icon and either log out or exit the process altogether.

---

### Post by ajgreeny on 2020-04-24
> **SeijiSensei said:**
> Usually when I kill the main Zoom window(s), the process continues to run with an icon in my task bar.  (I'm on KDE, though I'd imagine the same is true for other flavors of Ubuntu.)  I can right-click the icon and either log out or exit the process altogether.
Same here in Xubuntu 18.04, so have a look in the panel and see if you have the same icon sitting there.

EDIT:
I have now added a screenshot of the panel icon; it's the blue camera icon in the middle which I right click and use Exit.

---

### Post by dragonfly41 on 2020-04-24
[COLOR=#000000]> I've killed it multiple times by "ps aux"ing and killing the offending PID.

I do not yet use Zoom although I will need some similar functionality for a project but more secure.
I have read that [jami]("https://jami.net/") is worth researching.

Meanwhile if you are using Zoom perhaps install Docky since you can easily close down apps in Docky.
Another useful Dashboard is Stacer .. Process window.

[/COLOR]

---

### Post by ajgreeny on 2020-04-24
As a follow up to my post #3, I have used zoom this afternoon and much to my surprise, in spite of using Exit from the icon in my panel zoom was, as you suggested, continuing to run and use 25% of my cpu power.

***ps aux | grep zoom*** showed three instances of zoom still running
[LIST=1]
[*]/usr/bin/zoom
[*]sh -c export SSB_HOME=/home/<user>/.zoom; export QSG_INFO=1; export LD_LIBRARY_PATH=/opt/zoom; export BREAKPAD_CLIENT_FD=3; /opt/zoom/zoom ""
[*]/opt/zoom/zoom
[*]
[/LIST]
The third of those was the one using the cpu so much which I found by killing them one by one; the first two did not reduce cpu usage when killed, the third did.

Luckily I use zoom only very occasionally, and I now know to simply issue a ***killall zoom*** command to stop it completely, but nevertheless it is annoying that an application does not behave itself and stop running when you exit, as it should.

---

### Post by SeijiSensei on 2020-04-24
It all went away when I chose Exit from the icon.

Before
```

$ ps ax | grep -i zoom
 428663 ?        Sl     0:00 /usr/bin/zoom
 428670 ?        S      0:00 sh -c export SSB_HOME=/home/phl/.zoom; export QSG_INFO=1; export LD_LIBRARY_PATH=/opt/zoom; export BREAKPAD_CLIENT_FD=3; /opt/zoom/zoom ""
 428671 ?        SLl  1240:28 /opt/zoom/zoom
 547854 pts/8    S+     0:00 grep --color=auto -i zoom

```

After

```

$ ps ax | grep -i zoom
 547862 pts/8    S+     0:00 grep --color=auto -i zoom

```

---

### Post by TheFu on 2020-04-24
A helpful alias:
```
alias psg='ps -eaf | grep $*'
```

Another tool:
```
$ pgrep -a firef
30559 /usr/lib/firefox/firefox

```

---

### Post by goemonburo on 2020-04-25
Thank you all for the suggestions and help.  Alas, I was already looking for an icon in the taskbar and there isn't any.  And for example, right now, when I type:

    ps aux | grep zoom

I get nothing except the PID with the grep zoom.  Which means it SHOULD be gone.

What I'm talking about is that I will now walk away from my computer, the screensaver will come on, and when I return, unlock it, I guarantee there'll be a "Join Zoom Meeting" window open on my desktop.

Once I see that, I can click "close" and then the window disappears.  I can also kill it via the grep zoom and kill the PID.  

But something that I'm unaware of is causing it to respawn like a zombie in a B movie horror flick.  

(I suspect that what may be happening is the icon in the taskbar is somehow not showing up...and that icon may not have "zoom" as the PID???)

I'm not -- thus far -- experiencing any performance or slowness issues.  Only the Zoombie phantom rising like the Phoenix each time I login.

---

### Post by goemonburo on 2020-04-25
And yep, it happened again.  I "killall zoom"ed and it all vanished.  But I bet it will be baaaaaaaaaack.  (Terminator voice...)

---

### Post by TheFu on 2020-04-25
[http://zarnovican.github.io/2018/05/20/autostarting-zoom-app/](http://zarnovican.github.io/2018/05/20/autostarting-zoom-app/)
I don't have zoom and didn't test it.  Looks like zoom gets inserted as the "screen saver", so find where your screen saver choice is made, and put it back to the original?

---

### Post by dragonfly41 on 2020-04-25
Perhaps a sneaky cron job is tucked away somewhere?

---

### Post by goemonburo on 2020-04-25
Zoom was indeed checked in the screensaver, so I've unchecked it and have fingers (tightly!) crossed.  :-)

---

### Post by TheFu on 2020-04-25
> **goemonburo said:**
> Zoom was indeed checked in the screensaver, so I've unchecked it and have fingers (tightly!) crossed.  :-)

Blind squirrel locates a nut!  ;)  Please mark the thread as SOLVED - thread tools button upper right of this page. Really helps everyone in the community.

---

### Post by goemonburo on 2020-04-26
There are two things that may have fixed it:

1)  I did (as suggested) untick the "Zoom" option in the screensaver.
2)  I finally discovered, hiding inside the VNC session's toolbar, the Zoom icon...which I then clicked and "Exit"ed.  

After that, it seems to have not come back.  And there was much rejoicing.

---

### Post by ajgreeny on 2020-04-28
The suggestion in TheFu's link at [http://zarnovican.github.io/2018/05/20/autostarting-zoom-app/](http://zarnovican.github.io/2018/05/20/autostarting-zoom-app/) was a good start but the file mentioned is not in my Xubuntu 20.04 where it is instead in /etc/X11/app-defaults/XScreensaver, which is actually a link to XScreensaver-gl.

There is also a third similarly named file XScreensaver-nogl in the same folder which also had exactly the same zoom entry.  I commented out the zoom line in those three files and now wait to see if everything I've done stops the zoom application autostarting after use; here's hoping!

---

