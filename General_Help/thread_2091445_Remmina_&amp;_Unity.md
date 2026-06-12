---
title: "Remmina &amp; Unity"
date: 2012-12-05
forum: General Help
---

### Post by venomenus on 2012-12-05
Hi,

Does anyone else have any problems when using Remmina with unity in both 12.04 and 12.10?

The specific problem is that when using Remmina as an RDP client to a windows machine in full screen mode, when you minimize this, the unity panel and launcher disappears/becomes transparent until you click on the area where the launcher/panel is.

(as attached)

I have tested this on a cinnamon desktop and everything works as expected.

Thanks in advanced.

---

### Post by mattc1170 on 2013-02-08
venomenus:

I have been experiencing a variety of problems with Remmina and Unity.  I have seen the problem you describe before, but not recently.  My newest problem is that whenever I minimize a full-screen Remmina session, my desktop re-appears for an instant, but then a snapshot of the full screen Remmina session pops back up, filling the entire screen.  The snapshot disappears when I left click anywhere on the desktop.  This is kind of a pain in the ass though, because the click registers on whatever application is hiding behind the Remmina fullscreen image.

Other problems:

- The keyboard will randomly stop working inside of my RDP session.
- The Super and Alt keys will randomly get captured by Unity instead of by the RDP session.  I've found no consistent predictability in this behavior.

---

### Post by thermion on 2013-02-08
> **mattc1170 said:**
> venomenus:

I have been experiencing a variety of problems with Remmina and Unity.  I have seen the problem you describe before, but not recently.  My newest problem is that whenever I minimize a full-screen Remmina session, my desktop re-appears for an instant, but then a snapshot of the full screen Remmina session pops back up, filling the entire screen.  The snapshot disappears when I left click anywhere on the desktop.  This is kind of a pain in the ass though, because the click registers on whatever application is hiding behind the Remmina fullscreen image.

Other problems:

- The keyboard will randomly stop working inside of my RDP session.
- The Super and Alt keys will randomly get captured by Unity instead of by the RDP session.  I've found no consistent predictability in this behavior.

I can confirm all of this. That's why I'm using rdesktop again.

---

### Post by scarboni888 on 2013-05-30
That's a big 'me too' over here as well.

Ubuntu Desktop 64-bit with whatever version of Remmina you get by default or through the Ubuntu Software Centre whichever it was I don't remember.

All I know is I didn't do no fancy-pants compiling or adding some extra-Canonical software source to get it.

---

### Post by typhoon_tip on 2013-07-08
At last some good news...

Fix will come for Precise in version 5.24. Still not in the proposed repo, but it will be soon I hope... Annoyed by this problem for a few months now.

[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1064155](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/1064155)

---

