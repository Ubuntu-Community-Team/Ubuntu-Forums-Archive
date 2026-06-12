---
title: "start IRC client from terminal mode"
date: 2013-02-27
forum: General Help
---

### Post by goodbye-windows(tm) on 2013-02-27
Hi All,

I'm moving away from Yahoo and Google due to privacy violations and unwanted personal information gathering by them.

I'd like to refrain from logging into the google completely-thus much less tracking info is available to them.

Is there anyway to start an irc client from the terminal? I'd like it to start, automatically log into the freenode irc network, and move me to a private chat room I set up for friends and family.

It needs to be a single command or 2 at most, doing so automatically at boot up is preferred, but not absolutely necessary. 

In my case, I'd like to open XCHAT, have it connect to the Freenode IRC network and have it move me to channel XYZ.

Can it be done?

TY.

Art

---

### Post by papibe on 2013-02-27
Hi goodbye-windows(tm).

All possible. It's just a matter of what is more convenient to you.

XChat can be set up to go directly to your prefer server, and channel. You can even set your nickname and password so it can connect automatically. 

Once that is all set, the usual way to get it open as soon as you login would be to use 'Startup Applications'.

I don't see how calling it from the terminal can be more convenient, but in case you need it:
```
xchat
```
or
```
/usr/bin/xchat
```
Does that help? Let us know how it goes.
Regards.

---

### Post by unheeding on 2013-02-27
You can also check out irssi, it's a terminal based IRC client and the one that I personally prefer.

---

### Post by CaptainMark on 2013-02-27
you can have it start minimized by adding this to startup applications ```
xchat --minimize=2
```beware though it does have a window that pops up and vanishes really quickly, its not a major deal but if your finicky like me you'll hate that little flutter and it will flash in the system tray telling you its connected, ive yet to find an irc client that can automatically, gracefully and silently connect you to an irc network in the same way that say pidgin or empathy do for most chat networks when you login

EDIT: Thinking about it, Unity (spit here) doesn't use the system tray anymore so you may find that if you start it minimised then you cant actually access that instance of xchat

---

