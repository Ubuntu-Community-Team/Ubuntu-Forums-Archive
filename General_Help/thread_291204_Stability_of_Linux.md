---
title: "Stability of Linux??"
date: 2006-11-02
forum: General Help
---

### Post by Synapse56 on 2006-11-02
I'm running Dapper, all patched-up etc. 

I've noticed that sometimes Firefox crashes when I move my mouse but it doesn't just die, it flattens my entire machine. Mouse freezes, keyboard fails to respond etc...the entire box is locked. It's only happening in FF, rest of system works.

The only recourse is to power off/on.  It happened twice last night, however this isn't about firefox as such.  



My question really is:

I appreciate that all software has bugs, but how on earth can an 'isolated' application halt the entire OS?

I keep reading about how Linux is stable and a move away from the famous BSoD, but such claims are incorrect.

I'm not giving-up on Ubuntu, I actually love it, I'm just disappointed that there isn't that much difference between Linux & Doze...

---

### Post by Sef on 2006-11-02
> I appreciate that all software has bugs, but how on earth can an 'isolated' application halt the entire OS?


That is really rare.  I'm wondering if the problem lies with your install.  When did you install the Dapper?  Did you make any changes before these problems started?

> I keep reading about how Linux is stable and a move away from the famous BSoD, but such claims are incorrect.

Actually it is much more stable. You unfortunately have problem that goes beyond firefox.  I hope you are able to quickly resolve your problem without reinstalling Dapper.

---

### Post by Jussi Kukkonen on 2006-11-02
> **Synapse56 said:**
> I appreciate that all software has bugs, but how on earth can an 'isolated' application halt the entire OS?

I keep reading about how Linux is stable and a move away from the famous BSoD, but such claims are incorrect.

I'm not giving-up on Ubuntu, I actually love it, I'm just disappointed that there isn't that much difference between Linux & Doze...

It is possible, probable even, that this is a driver problem and for some reason Firefox is the only thing that happens to trigger it. That would explain the system wide effects... Just to give you another data point on the stability: my three machines (two 8 year old laptops and one newer server) stay up for as long as I care to keep them running, no crashes.

Have you checked if there's anything in the logs (e.g. /var/log/syslog)? Have you tried if virtual consoles are usable when a crash happens (ctrl-alt-F1)?

---

### Post by theslut on 2006-11-02
the problem is probably xorg.  with no gui running , linux is extremely stable but running gnome or kde can bring the occasional hung window.

---

### Post by theosib on 2006-11-02
When the system is flattened, can you move the mouse pointer?  

It is possible to completely take over the server, locking out other applications.  It's called XGrabServer().  Applications aren't really supposed to do it except under unusual modal situations.  There are a few other grabs that apps can do.  The point is that it's possible to make your GUI look completely frozen, when in fact, a bad application has just taken over.

I've seen apps hang up during a server grab, and Firefox was one of them.  I've also had Konqueror hang up when running Flash.

I think there may be a way to break a grab, but I don't recall what it is.  But I have had some success with pressing Alt-Tab in a few cases.

Are you able to Ctrl-Alt-F1 (or is it Shift-Alt-F1?) to another system console?

What happens if you press Ctrl-Alt-Backspace (which is supposed to kill the X server)?

What would be really cool is if you could switch to another console and diagnose what's going on, like run "top" and see if Firefox is using a lot of CPU.  Or run vmstat (I for get the options, but I think "2" is what I remember using) to see if a lot of swapping is going on.

It's very important that you report these problems to Mozilla on their bug tracker.

---

