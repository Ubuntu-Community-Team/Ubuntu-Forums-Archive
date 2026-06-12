---
title: "VNC screen goes black when users try to switch accounts (what remote desktop to use?)"
date: 2018-05-21
forum: General Help
---

### Post by codingpug on 2018-05-21
My engineering team has four special shared computers running a mix of Ubuntu Desktop 16.04 and 18.04 that are in a lab that's a 5-minute walk from our cubes. We need remote desktop access for these machines (we have graphical test tools that can't be run in a SSH session, for example), and we want to be able to use separate user accounts on these systems so we can have separate shares/user directories, etc.

I've tried both Vino and x11vnc. Both of these solutions work fine for a single Ubuntu user account only, but the moment a logged-in VNC user tries to switch to their personal Ubuntu account (when the Ubuntu user selection screen appears), the VNC screen goes black and no keyboard/mouse controls have any effect on the remote system. If I go up to the lab and manually switch back to the original user account on the physical PC, then the VNC session becomes usable again.

Things I have tried:
[LIST]
[*]Tried Ubuntu 16 vs 18, and x11vnc vs. Vino.
[*]Configured x11vnc to start at boot (unlike the default Vino setup which only starts after a user with Vino configured logs on). I can log into any ubuntu user account over VNC when I do this, but once I'm logged in, any attempt to switch to another ubuntu account results in the black screen problem for the VNC client. So basically VNC is good for a single user-specific session and then it requires either manual intervention in the lab or a reboot to reset X11vnc to a usable state.
[*]Configured Vino to use unique ports for each user instance, then manually logged in to all local user accounts (starting their Vino server instances). This was interesting because only one VNC session was usable at a time (only one could interact with the computer, others either had a black or frozen screen). But the moment I tried to switch accounts, again, all VNC clients became unusable. If I manually switched to one of the other logged in accounts, that user's VNC session would become interactive/usable.
[/LIST]

My questions:
[LIST]
[*]Is it possible to change this behavior where the user selection screen breaks VNC clients?
[*]Is there a different Ubuntu 16/18-compatible remote desktop client that would allow graphical remote desktop in a multi-user environment? (I think TeamCity might work, however that's unfortunately a banned tool in our environment.)
[/LIST]

Thanks!

---

### Post by nlee2 on 2018-05-21
Will you share your x11vnc config?

Is x11vnc running with -share -forever switch?

---

### Post by codingpug on 2018-05-22
> **nlee2 said:**
> Will you share your x11vnc config?

Is x11vnc running with -share -forever switch?
I followed the steps [in this article]("http://c-nergy.be/blog/?p=8984") to install and configure x11vnc.

The resulting config looks like this:[INDENT][FONT=courier new][Unit]
Description=Start x11vnc at startup.
After=multi-user.target

[Service]
Type=simple
ExecStart=/usr/bin/x11vnc -auth guess -forever -loop -noxdamage -repeat -rfbauth /etc/x11vnc.pass -rfbport 5900 -shared

[Install]
WantedBy=multi-user.target[/FONT]
[/INDENT]

"forever" and "shared" are among the switches used, it looks like.

---

### Post by nlee2 on 2018-05-22
Thanks for the info. Have you tried tigervnc-standalone-server? It can be  configured to assign a port per user.

VNCSERVERS="1:user1 2:user2"

---

