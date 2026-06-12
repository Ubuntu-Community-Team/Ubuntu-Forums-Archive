---
title: "Updated to 13.10, windows have no 'control' bar (e.g. min/max/close buttons)"
date: 2013-11-10
forum: General Help
---

### Post by qf-ryan-nr on 2013-11-10
Windows in most of many of my programs now have no frame that I can use to resize/close them. It also appears that I can't resize them manually, the frame where I'd click is gone. I've attached a photo of the behavior. There are three windows open here. You can see the top bar where I'd typically be able to control the windows is missing. Any advice?

[http://i.imgur.com/GQypvFR.png?1](http://i.imgur.com/GQypvFR.png?1)

---

### Post by bapoumba on 2013-11-10
Hello and welcome to the forums.
I've removed the large image and kept the url.
Is the system up to date ? There are a few older bugs lying around.

---

### Post by ardchoille422 on 2013-11-10
> **qf-ryan-nr said:**
> Windows in most of many of my programs now have no frame that I can use to resize/close them. It also appears that I can't resize them manually, the frame where I'd click is gone. I've attached a photo of the behavior. There are three windows open here. You can see the top bar where I'd typically be able to control the windows is missing. Any advice?

[http://i.imgur.com/GQypvFR.png?1](http://i.imgur.com/GQypvFR.png?1)

Looks like you've somehow lost your window manager, or it isn't running. The window manager is responsible for drawing the frame and titlebar for each window.

---

### Post by qf-ryan-nr on 2013-11-10
I checked my env and it says my XDG_CURRENT_DESKTOP=Unity, which I think means Unity is my window manager right now. So this appears to be some sort of Unity issue? Any idea how to troubleshoot this? Some windows (e.g. Google Chrome) have their tollbars...

Also, in response to Bapoumba: The system is up to date, and thanks for editing my post to conform to local norms.

---

### Post by qf-ryan-nr on 2013-11-10
For future searchers: I followed the Unity/Compiz reset instructions here and this seems to have addressed the problem: [http://ubuntuhandbook.org/index.php/2013/08/reset-unity-and-compiz-in-ubuntu-13-10/](http://ubuntuhandbook.org/index.php/2013/08/reset-unity-and-compiz-in-ubuntu-13-10/)

---

### Post by stinkeye on 2013-11-10
Does it happen often?
Does log out/in solve.

In the terminal try....
```
/usr/bin/gtk-window-decorator --replace & disown
```
Ocassionally I will lose decorations which can be solved by the above command or
reload unity with
```
setsid unity
```

You can do as in the link you posted but then you will lose any 
customizations to compiz you may have done.
After a release upgrade though, it may be wise to set compiz back to defaults.

---

### Post by bapoumba on 2013-11-11
> **qf-ryan-nr said:**
> ..
Also, in response to Bapoumba: The system is up to date, and thanks for editing my post to conform to local norms.
Welcome!

> **qf-ryan-nr said:**
> For future searchers: I followed the Unity/Compiz reset instructions here and this seems to have addressed the problem: [http://ubuntuhandbook.org/index.php/2013/08/reset-unity-and-compiz-in-ubuntu-13-10/](http://ubuntuhandbook.org/index.php/2013/08/reset-unity-and-compiz-in-ubuntu-13-10/)

One additional recommendation if I may : mark your thread as solved (in the Thread Tools menu), thanks :)

---

