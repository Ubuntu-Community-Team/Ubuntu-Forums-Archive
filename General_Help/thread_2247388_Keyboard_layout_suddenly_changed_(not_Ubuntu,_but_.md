---
title: "Keyboard layout suddenly changed (not Ubuntu, but Zorin OS 9)"
date: 2014-10-07
forum: General Help
---

### Post by Christian.Hamburg on 2014-10-07
Hi there!

I know this forum is about Ubuntu, but I posted this question in the Zorin forum a few days ago and did not get an answer yet. And since Zorin is based on Ubuntu I thought I'd give it a try here...

So I installed Zorin OS 9 on my laptop and everything is fine, it runs like a charm. But I have a problem with my keyboard layout. I'm using a german keyboard (QWERTZ), and when asked during the installation I chose the appropriate layout.
Everything worked fine, but suddenly (days with shutdowns and boots later) the layout changed, out of the blue as it seems. Now I type "Z" when I actually want a "Y". In my dock I can change this back to the german layout, but I have to do this every time after I boot up. The strange thing is, that this reverted all of a sudden, without me knowingly doing anything, as I said before.

Since I'm rather new to Ubuntu, Zorin OS and Linux altogether, can someone help me? I just want the OS to start with a german layout. I still have to find my way around what files and scripts are essential, and where to configure all of this.

Thanks a lot
Christian

---

### Post by matt_symes on 2014-10-07
Hi

I'm not familiar with Zorin however you should be able to set the keyboard mapping using

```
setxkbmap
```

This will not persist after a reboot though unless you call it from a script at each boot.

Anyway, I'm interested in the desktop environment that Zorin uses.

Open a terminal and copy and paste this in it.

```
env | grep DESKTOP
```

Copy and paste the output from the terminal into you next post.

From there we can, hopefully, make headway into why it's being reset after each reboot.

Kind regards

---

### Post by Christian.Hamburg on 2014-10-07
OK, thanks. This is the output:

DESKTOP_SESSION=zorin_desktop
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
XDG_CURRENT_DESKTOP=Unity

Regards

---

