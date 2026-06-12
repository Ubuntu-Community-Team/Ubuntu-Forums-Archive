---
title: "SSH and x11 applications"
date: 2005-08-16
forum: General Help
---

### Post by nophix on 2005-08-16
I want to ssh to my main computer and have x-chat to display on my other computer from the main computer. Is this possible via ssh?

(I know vnc exist)

---

### Post by endy on 2005-08-16
"ssh -X" should do the trick, from the manpage:

>  -X      Enables X11 forwarding.  This can also be specified on a per-host basis in a configuration file.

I think that's all you need :)

---

### Post by nophix on 2005-08-16
Oh sorry, I described it wrong.

I mean, when I have x-chat running on my main computer, can I have that process showing up on my other computer too?

---

### Post by kvidell on 2005-08-16
[QUOTE=nophix]Oh sorry, I described it wrong.

I mean, when I have x-chat running on my main computer, can I have that process showing up on my other computer too?[/QUOTE]
 You'd need to forward a VNC session. I don't think you can "Detatch" X apps like you can a Screen Session.

Run it in VNC and just leave that VNC session someplace handy with XChat in it. Shell in with -L5950:localhost:5950 (or whatever your VNC port is) then connect your VNC viewer to localhost:50 I believe. (I used to do it and had a VMWare session running with XP Pro SP2 off my file server for a few reasons. It was _really_ useful.)

I just use BitchX though when it comes to IRC. It's a little bit easier to get working "Anywhere". I've had the same session open for something like 5 months now? It just hangs out in a screen session on my friends BSD box.
- Kev

---

### Post by nophix on 2005-08-16
[QUOTE=kvidell]You'd need to forward a VNC session. I don't think you can "Detatch" X apps like you can a Screen Session.[/QUOTE]

Like I said before, I knew about vnc. :)
Was just thinking if ssh was this flexible.

[QUOTE=kvidell]
I just use BitchX though when it comes to IRC. It's a little bit easier to get working "Anywhere". I've had the same session open for something like 5 months now? It just hangs out in a screen session on my friends BSD box.
- Kev[/QUOTE]

Yes, I used to do that with irssi. But I have other applications like gaim and vmware for example. :)

---

