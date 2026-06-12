---
title: "Screen Sharing and screen recording problem on Ubuntu 21.04 (wayland)"
date: 2021-06-05
forum: General Help
---

### Post by thedoer on 2021-06-05
Hi Community!
I have moved to Ubuntu 21.04 about half a month ago from 20.10. In 21.04, I have been encountering so much issues. 

1. I can't share screen using google meet, viewer can't see my screen rather an [COLOR=#ff0000]**entirely black screen**[/COLOR] (A window sharing works fine).
2. Screen recording apps e.g. Kazam, OBS studio[COLOR=#ff0000] **can't record my entire screen only black screen appears**[/COLOR] (window recording works fine).
3. When I pressed windows key, sometimes my **[COLOR=#ff0000]PC got stuck,[/COLOR]** I cannot go anywhere then. Thereafter I have to forcefully shut down my PC to start using it again.

Much appreciation for any kind of solution.
Thanks.

---

### Post by coffeecat on 2021-06-05
Support, not chat.

*Thread moved to **General Help**.*

---

### Post by ActionParsnip on 2021-06-05
Are you using Wayland or Xorg?

---

### Post by TheFu on 2021-06-05
> **ActionParsnip said:**
> Are you using Wayland or Xorg?

The title says Wayland.  I did see that OBS started supporting Wayland at some level last week. Don't know what that support actually means.  The OBS version definitely isn't part of any OBS in a repo.  Perhaps there is a PPA with the newest version?

If I were the op and didn't want to troubleshoot Wayland problems, I'd just revert to X11 and be happy. To configure Xorg as the default GNOME session. Open the custom.conf 
```
sudoedit  /etc/gdm/custom.conf 
```
and uncomment 
```
WaylandEnable=false 
```
if it's commented but must be set to false. Reboot.

21.04 is a bleeding edge release.  21.10 will be bleeding as well.  Stick with LTS releases only to minimize surprises, though those still happen.

For a long time, there was only 1 tool that could capture a screen. It was a Gnome tool and dependent on gstreamer. Meh. I much prefer SimpleScreenRecorder.

---

### Post by entropy1 on 2021-06-05
Thank you!

Switching to X11 in 21.04 allowed me to share my screen in MS Teams. I had been unable to do that with Wayland.

Also, on my system, there is no /etc/gdm, but I found the custom.conf file in /etc/gdm3

---

### Post by TheFu on 2021-06-05
Glad it helped you figure out.  

If this is solved, please help the community - Mark it a SOLVED - "Thread Tools" Button near the top of the page ---> SOLVED.

---

### Post by HermanAB on 2021-06-06
Hmm, when programmers look at a complex wheel and think they can quickly make a much simpler and better one, they invariably invent a triangular wheel, followed by a square wheel...  Wayland is now maybe a hexagon and Xorg still works much better with remote sessions.

---

### Post by thedoer on 2021-06-06
echo $XDG_SESSION_TYPE says it's wayland.

---

### Post by thedoer on 2021-06-06
[COLOR=#000000]Reverted to X11 and seems everything works fine. Thanks. By the way, for my case it was "gdm3" Thank you.[/COLOR]

---

