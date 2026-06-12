---
title: "Nomachine NX server no longer working on 12.10"
date: 2012-11-13
forum: General Help
---

### Post by edwardecl on 2012-11-13
I just updated from 12.04 and nxserver works... but it drops the connection after you see the desktop background...

I've tried forcing it to load other desktop (XFCE) but it does the exact same thing with the with blue background popping up before is goes bye bye.

Is NX just broken till they fix it or is there some sort of configuration I can do to fix it... the logs don't help me much either.

It seems every update breaks NX in some way :(. Wish there was another remote desktop as good as NX that just works as it should...

VNC requires your machine to be running X all the time, which I don't do as my computer does not have a graphics card plugged in...

---

### Post by MidnightJava on 2012-11-15
NX is not working for me after upgrading to 12.10 also (from 11.10). I found [this post]("http://www.nomachine.com/tr/view.php?id=TR10J02752") which explains a problem and a workaround. This didn't work for me, but maybe it will for you. Also my problems seems to be different. I can't get the NX server to work at all. When I query its status on the system where it's running, it says authentication failed and the server is not running.

I noticed that the NX download site mentions 12.04 as the latest Ubuntu version supported, but the post I linked to above suggests 12.10 working for someone.

---

### Post by QIII on 2012-11-15
This is one of the reasons I am not running Quantal as my primary machine right now.

Sigh.

I don't know that I would expect a solution from NoMachine any time soon either, since they are heavily involved in actively dragging their feet on the development of 4.0.  4.0 Preview 6 has been available for something like a year and it's still a 60 or 90 day trial last I checked.

---

### Post by MidnightJava on 2012-11-16
I found [this thread]("http://ubuntuforums.org/showthread.php?t=1490038&highlight=nxserver") which solves my authentication problem, but now I'm at the place you are--the session starts and then goes away after showing the desktop briefly.

I've tried KDE as well as custom sessions using "/etc/X11/Xsession gnome-session-fallback" for the command. None of this works, except that one time I got the KDE desktop to come up. I've tried it a dozen times since then, and I can't get it to come up again. I'm using the same settings I did when it worked, so I have no idea why it came up that one time.

---

### Post by MidnightJava on 2012-11-16
The simple fix in [this post]("http://ubuntuforums.org/showthread.php?t=2081746&highlight=nomachine") worked for me, combined with the fix linked in my previous post, wherein the fallback desktop environment is configured as "GNOME Classic (without effects)" in the NX node config file. I set the desktop to GNOME on the NX Client configuration dialog. It's not Unity, but it works fine.

---

### Post by fatpenguin on 2012-11-17
It really seems as if NX is going to have a rough time supporting future iterations of the full desktop environment as GNOME and Unity continue down the path of providing more complex UIs involving graphics hardware.

Due to this, I've reverted to finding other solutions, and am currently running XMing and signing in this way.  I'll always miss the ability to leave sessions running, but otherwise I've actually found that I like this more, but am open to other options.

XMing fails to launch compiz via XDMCP for me, but has anyone tried running through Xephyr or Xnest as a solution for this?

---

### Post by cu_ on 2012-11-23
I spent an entire day trying to resolve this issue.  I followed every suggestion on this thread and links in this thread.  Finally gave up and went back to NoMachine 3.5.  Preview 4 simply does not play with 12.10.  Since ubuntu 12.10 got release while Nx 4 is still in preview, I am hoping they will have a chance to iron out things.  I am excited about the features available in Preview 4.

---

