---
title: "vncviewer not working"
date: 2007-04-19
forum: General Help
---

### Post by sgardne on 2007-04-19
Hello all,

I'm setting up a new install for my brother, and I want to be able to use reverse vnc connections via vncconnect so that I can easily provide tech support to him in the future. It is apparently not working for me however, so I did a little testing and a lot of reading, but I've not been able to get it happening for me. Here's what I'm trying now:

On his box, I'm initiating vncserver, and it gives me the message that it is working. 

On my box, I attempt to connect using vncviewer, and it connects, I type in the password, and it opens the display, but it's just greyed out with an X mouse cursor. (See attached screenie).

Like I said, it seems to be connected, but there's no display, and I'm not controlling anything. 

Both boxes are Feisty. I am using the non-free ATI drivers if that matters.

---

### Post by fanatik on 2007-04-20
I think you'll find that it *IS* working! You probably don't have vncserver configured to start any programs, which is why you're seeing a grey screen. vncserver opens a new dislpay for you, on which you can run programs, xterm, GDM, etc. I guess you were expecting to see his desktop.

I tried to get vncserver working and for it to start a new Gnome session etc, but gave up after a while. Fortunately Gnome has a nice simple built-in solution for you... :)

On your brothers machine, go to System->Preferences->Remote Desktop and select 2 check boxes, allowing other users to view and control your desktop. if you uncheck the 'ask for confirmation' box you can connect even when he is not sat at his pc, otherwise he has to click allow for any connections coming in. Enter a suitably secure password and you're done!

That will allow you to connect to Display 0, ie his desktop, using any vnc viewer.

:)
James.

---

### Post by sgardne on 2007-04-20
> **fanatik said:**
> I think you'll find that it *IS* working! You probably don't have vncserver configured to start any programs, which is why you're seeing a grey screen. vncserver opens a new dislpay for you, on which you can run programs, xterm, GDM, etc. I guess you were expecting to see his desktop.

I tried to get vncserver working and for it to start a new Gnome session etc, but gave up after a while. Fortunately Gnome has a nice simple built-in solution for you... :)

On your brothers machine, go to System->Preferences->Remote Desktop and select 2 check boxes, allowing other users to view and control your desktop. if you uncheck the 'ask for confirmation' box you can connect even when he is not sat at his pc, otherwise he has to click allow for any connections coming in. Enter a suitably secure password and you're done!

That will allow you to connect to Display 0, ie his desktop, using any vnc viewer.

:)
James.
Okay that did work! Progress yay! I'd really like to get reverse connections working though since I won't have access to his wireless router which is 400 miles away, and he won't have the technical know-how to configure it himself. I think your suggestion about the applications maybe the key though. Thank you for this.

---

