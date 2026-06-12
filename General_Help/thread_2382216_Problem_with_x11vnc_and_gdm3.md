---
title: "Problem with x11vnc and gdm3"
date: 2018-01-10
forum: General Help
---

### Post by stian-dalviken on 2018-01-10
Hi all,

I'm new to this forum and a fairly limited Linux user, so please be gentle :)

First of all I had an issue where my Ubuntu desktop wouldn't boot into the login screen, and only displayed a black screen with the text that said something like "problem with lvmetad". I have tried a bunch of things to make it boot normally, but no luck. Eventually I tried changing the default display manager from lightdm to gdm3, and suddenly it booted up fine.
But now I have an interesting case where I'm only able to remotely connect via VNC when the default display manager is set to lightdm, but Ubuntu won't properly boot while using that display manager. When I'm using gdm3 I only getting a "connection refused" on the remote device when trying to connect via VNC...

Has anyone experienced something similar, or know how to fix this issue?

---

### Post by treii28 on 2018-04-30
> **stian-dalviken said:**
> Hi all,

I'm new to this forum and a fairly limited Linux user, so please be gentle :)

First of all I had an issue where my Ubuntu desktop wouldn't boot into the login screen, and only displayed a black screen with the text that said something like "problem with lvmetad". I have tried a bunch of things to make it boot normally, but no luck. Eventually I tried changing the default display manager from lightdm to gdm3, and suddenly it booted up fine.
But now I have an interesting case where I'm only able to remotely connect via VNC when the default display manager is set to lightdm, but Ubuntu won't properly boot while using that display manager. When I'm using gdm3 I only getting a "connection refused" on the remote device when trying to connect via VNC...

Has anyone experienced something similar, or know how to fix this issue?

I'm running into similar problems and it seems that the new gdm3 may create a new display when a user logs in. I'm still digging into how one might access that or if there's a recommended way to handle this with VNC. I haven't found any good responses yet.  Have you tried using the 'desktop sharing' option? (that is what I normally use but I can't seem to get it to enable properly remotely)

---

