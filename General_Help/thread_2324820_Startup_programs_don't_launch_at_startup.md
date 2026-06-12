---
title: "Startup programs don't launch at startup"
date: 2016-05-16
forum: General Help
---

### Post by bullywug on 2016-05-16
I'm finding that programs that should be launching at startup are not reliably doing so.  Sometimes Variety launches okay but My Weather Indicator won't launch at startup nor will Cairo.  Both require me to manually launch them each time the machine starts.  This weekend I actually reinstalled Ubuntu but the problem persists.  I did to a restore of my home directory using the built in backup app.  I've searched alot for this and I can't figure it out.

I almost forgot to mention, I don't know if this is related but the my weather indicator in the toolbar shows a question mark but it seems to be updating.  I'm wondering if I should create a new account and just copy my files over.

---

### Post by howefield on 2016-05-17
> **bullywug said:**
>  Sometimes Variety launches okay...

For Variety follow this bug.. [https://bugs.launchpad.net/variety/+bug/1579484](https://bugs.launchpad.net/variety/+bug/1579484) assuming you are not the reporter :)

> I almost forgot to mention, I don't know if this is related but the my weather indicator in the toolbar shows a question mark but it seems to be updating.  I'm wondering if I should create a new account and just copy my files over.

What is the name of the weather app ?

---

### Post by vasa1 on 2016-05-17
Would it help if you stagger the loading of autostart apps by sticking in a sleep period?

---

### Post by bullywug on 2016-05-17
Thanks for the info.  So Variety is a bug and will have to be manually launched until it is fixed (just confirming that I understand correctly).  The weather app is my-weather-indicator and it started showing the weather without the question mark but again, it won't launch on startup.  I can however manually launch it.  Another thing that I'll mention because I think its related: Nylus N1's indicator no longer shows up in the menu bar. I'm including a screen shot of Nylus settings screen.

[https://onedrive.live.com/redir?resid=D748338BC411C1A3!376298&authkey=!AFY2Rkeh6AV8zEY&v=3&ithint=photo%2cpng](https://onedrive.live.com/redir?resid=D748338BC411C1A3!376298&authkey=!AFY2Rkeh6AV8zEY&v=3&ithint=photo%2cpng)

---

### Post by bullywug on 2016-05-17
@Vasa1

I don't know.  My feeling is that it wouldn't help.  I don't have very many things launching at startup, but I could try that.

---

### Post by bullywug on 2016-05-21
> **vasa1 said:**
> Would it help if you stagger the loading of autostart apps by sticking in a sleep period?

I tried delaying the applications by 30 seconds each.  When I restarted, nothing loaded.  :(
Any other suggestions?  Is my install busted for some reason?

---

