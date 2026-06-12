---
title: "Unwanted NetworkManager Applet messages"
date: 2023-05-26
forum: General Help
---

### Post by DavidS on 2023-05-26
I recently installed Ubuntu Unity 23.04, replacing 22.04.

Now every time I wake to the computer after a "suspend", I have several on-screen messages from NetworkManager Applet telling me that I am now off-line.  This is not true, but presumably it was true for a few seconds after waking.  Sometimes there is also one message telling me that I am now online.  I have tried clicking on "Don't show this message again", but that hasn't helped.

How can I stop these messages from appearing - or, better still, how can a set a delay before they appear?  It would be useful to know if I am offline, but not when it is simply because the system hasn't had time to reconnect after being suspended.

---

### Post by TheFu on 2023-05-26
Desktop or laptop system?
For a desktop, having any network applet is pretty useless.  Just purge it from the system.
For a laptop, there are other tools besides network-manager that can be used to control connections.

I have to ask, why would someone migrate from an LTS release, 22.04, to a non-LTS release 23.04?  Now you must upgrade every 6 months until 24.04 is released. That will be the next LTS with either 3 or 5 yrs of standard support.  If 22.04 was working for you, new isn't necessarily better.  Heck, I just moved an 18.04 system to 20.04 last week.  I had to because standard support for 18.04 was ending.  The computer was extremely stable, but getting security patches was my driver to migrate and a few features related to LXD and KVM/QEMU support, definitely not for networking or a prettier GUI.

---

### Post by DavidS on 2023-05-27
Thanks for the reply.  Desktop system.

Yes, I suppose purging the applet is one way of dealing with the problem, but it's quite nice to have it there as confirmation that I am online.  It's the popup messages that I would like to get rid of, or better still control the offline time that elapses before the message appears.

As regards the support time for various Ubuntu releases, I am familiar with all those details.

---

### Post by deadflowr on 2023-05-27
See if
```
gsettings set org.gnome.nm-applet disable-disconnected-notifications true
gsettings set org.gnome.nm-applet disable-connected-notifications true
```
disables it for you.

---

### Post by DavidS on 2023-05-27
Yes, thank you.  That worked!

---

### Post by mIk3_08 on 2023-05-28
> **DavidS said:**
> Yes, thank you.  That worked!

If your query has been sorted then you can mark this thread as solve.
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

