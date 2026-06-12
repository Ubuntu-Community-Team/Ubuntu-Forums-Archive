---
title: "is it true that SNAP always runs?"
date: 2020-05-05
forum: General Help
---

### Post by anotherChris on 2020-05-05
Is it true that once you install any snap program, it always runs in the background?

---

### Post by Holger_Gehrke on 2020-05-05
No. The snapd background process always runs if your system is set up to use snaps independent of whether there actually are any programs installed as snaps. This offers various services related to installing, updating, running and removing snaps. Programs installed as snaps only run in the background if that's the way they were designed to be run.

Holger

---

### Post by anotherChris on 2020-05-05
> **Holger_Gehrke said:**
> 
[QUOTE=anotherChris;13953989]Is it true that once you install any snap program, it always runs in the background?
No. The snapd background process always runs if your system is set up to use snaps independent of whether there actually are any programs installed as snaps. 
[/QUOTE]

Mmmm. Okay. I installed Lubuntu 20.04 without installing any programs yet, but I can't see snapd running with Cntrl+Alt+Delete or with ps -x or ps -e

---

### Post by deadflowr on 2020-05-06
> **anotherChris said:**
> Mmmm. Okay. I installed Lubuntu 20.04 without installing any programs yet, but I can't see snapd running with Cntrl+Alt+Delete or with ps -x or ps -e

You can check he snapd service status with
```
systemctl status snapd
```
(press q to exit)

---

### Post by anotherChris on 2020-05-11
> **deadflowr said:**
> You can check he snapd service status with
```
systemctl status snapd
```

Okay, but when I do that, I get...

```

&#9679; snapd.service - Snap Daemon
     Loaded: loaded (/lib/systemd/system/snapd.service; enabled; vendor preset: enabled)
     Active: inactive (dead) since Mon 2020-05-11 08:27:14 JST; 13h ago
TriggeredBy: &#9679; snapd.socket
    Process: 653 ExecStart=/usr/lib/snapd/snapd (code=exited, status=42)
   Main PID: 653 (code=exited, status=42)

 5&#26376; 11 08:26:15 ptr systemd[1]: Starting Snap Daemon...
 5&#26376; 11 08:26:28 ptr snapd[653]: AppArmor status: apparmor is enabled and all features are a>
 5&#26376; 11 08:26:33 ptr snapd[653]: daemon.go:343: started snapd/2.44.3+20.04 (series 16; class>
 5&#26376; 11 08:26:33 ptr snapd[653]: daemon.go:436: adjusting startup timeout by 30s (pessimisti>
 5&#26376; 11 08:26:41 ptr systemd[1]: Started Snap Daemon.
 5&#26376; 11 08:27:14 ptr snapd[653]: daemon.go:539: gracefully waiting for running hooks
 5&#26376; 11 08:27:14 ptr snapd[653]: daemon.go:541: done waiting for running hooks
 5&#26376; 11 08:27:14 ptr snapd[653]: daemon stop requested to wait for socket activation
 5&#26376; 11 08:27:14 ptr systemd[1]: snapd.service: Succeeded.

```

I can see from the second line that Snap is enabled, but from the third line, it looks like it is "inactive".  Is that not because I have not yet installed any Snap programs?   Or, if I did install a Snap program but then didn't run it at all, would it also say "inactive", or would it be "active" because some Snap program is installed?

---

### Post by deadflowr on 2020-05-11
Unfortunately the output cuts off,
you can get around that by piping (? is that the right term) the output to a file
```
systemctl status snapd >> snapd-status.txt
```

But from the limited output it shows that something is off with the socket activation, so it simply stopped the daemon.
Could this be because of no snaps installed? I don't know.
Any system I have without any snaps has no snapd either.

---

### Post by anotherChris on 2020-05-12
> **deadflowr said:**
> it shows that something is off with the socket activation, so it simply stopped the daemon.
Could this be because of no snaps installed? I don't know.
Any system I have without any snaps has no snapd either.

Okay.  :-k

---

