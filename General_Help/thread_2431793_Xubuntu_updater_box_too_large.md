---
title: "Xubuntu updater box too large"
date: 2019-11-21
forum: General Help
---

### Post by mauser9069 on 2019-11-21
I am using Xubuntu 18.04 LTS which I have only one issue. When I get updates the updater box is way too wide and can't be resized. I have the DPI set to 160 because of my eyesight. Everything renders correctly except for the updater as you can see here [https://postimg.cc/w7Fk6QvD]("https://postimg.cc/w7Fk6QvD") and here. [https://postimg.cc/n9j7jLkB]("https://postimg.cc/n9j7jLkB")
How do I get these dialog boxes to resize so it fits the screen?

---

### Post by vanadium on 2019-11-22
A slight decrease in your DPI setting is not an option? (e.g., combined with a slight increase in font size). Anyway, you still will be able to change the size of the window by hitting the <Alt> key and dragging near the window edges. The new size unfortunately will not remembered. Still, if needed, you could use a tool such as devilspie (or devilspie2) that allows to automatically size and place windows that match your criteria.

---

### Post by mauser9069 on 2019-11-22
I tried reducing the DPI a little and it was still way too large. <Alt> key and dragging doesn't resize it, it only moves the dialog box. Every time there is an update I have to move the dialog box to gain access to the buttons. Thank you for letting me know about devilspie and devilspie2 but I can't get either one of them to work. I am commandline illiterate. I looked them up on the Internet and I can't get either one of them to work. It says there is a G.U.I. version called [gdevilspie]("http://code.google.com/p/gdevilspie/") but it comes in a tar ball that doesn't tell me where I am suppose to open that tar ball to.

---

### Post by vanadium on 2019-11-22
<Alt>key and *left* button dragging will indeed move. However, <Alt>key + *right* button dragging should, under Xubuntu, resize. Unless the window cannot be resized. You may try the approach on another window, such as the file manager. Anyway, if this only concerns the updater, you can probably deal with moving and clicking. Then it may not be worthy investigating more complex solution.

Edit: another valid way for you may be to run the system on a lower resolution. Then you can set dpi and font size to default. The lower resolution will render all UI elements larger, and in proportion. Yet, if the resolution gets too low, many dialogs by default will not anymore fit the screen.

---

### Post by mauser9069 on 2019-11-22
It doesn't resize even by  <Alt>key + *right* button dragging. Looks like I have to find where I can file a bug report on this. In the mean time I will have to move around the dialog boxes.

---

### Post by mauser9069 on 2019-11-22
Edit: Bug report filed.

---

### Post by mörgæs on 2019-11-22
Please link to it.

---

### Post by mauser9069 on 2019-12-06
> **mörgæs said:**
> Please link to it.

Sorry for replying so late because I never received an E-mail notification on your reply. This is what I am talking about. [https://postimg.cc/w7Fk6QvD](https://postimg.cc/w7Fk6QvD) and here. [https://postimg.cc/n9j7jLkB](https://postimg.cc/n9j7jLkB)

---

### Post by yetimon_64 on 2019-12-06
> **mauser9069 said:**
> Edit: **Bug report** filed.

> **mörgæs said:**
> **Please link to it**.

> **mauser9069 said:**
> Sorry for replying so late because I never received an E-mail notification on your reply. This is what I am talking about. [https://postimg.cc/w7Fk6QvD](https://postimg.cc/w7Fk6QvD) and here. [https://postimg.cc/n9j7jLkB](https://postimg.cc/n9j7jLkB)

mörgæs was asking you to link to a bug report on launchpad.net. launchpad.net is the site where bugs in ubuntu are logged for further action. You are just linking to images of your problem, which is NOT a bug report by any means.

Have you really logged a bug for this on launchpad.net? If you have, a link to it on launchpad is what was asked for.

If needed, [[COLOR=#0000ff]--here--[/COLOR]]("https://ubuntuforums.org/showthread.php?t=1011078") (link in blue text) is a link to a guide on this forum for making bug reports.

Regards, yeti.

---

### Post by Dennis N on 2019-12-06
For vision problems, there is the xubuntu screen zoom feature: 
First, set your dpi to normal.
Then,
Alt + Mouse Wheel forward will zoom screen. 
Once zoomed, Move mouse left edge and right edge and top to bottom to view desktop.
Alt + Mouse Wheel back will reduce zoom.

Is that useful?

---

### Post by mauser9069 on 2019-12-06
> **yetimon_64 said:**
> mörgæs was asking you to link to a bug report on launchpad.net. launchpad.net is the site where bugs in ubuntu are logged for further action. You are just linking to images of your problem, which is NOT a bug report by any means.

Have you really logged a bug for this on launchpad.net? If you have, a link to it on launchpad is what was asked for.

If needed, [[COLOR=#0000ff]--here--[/COLOR]]("https://ubuntuforums.org/showthread.php?t=1011078") (link in blue text) is a link to a guide on this forum for making bug reports.

Regards, yeti.

Thank you for clarifying it. I misunderstood the question. [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1853619](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1853619)

---

### Post by yetimon_64 on 2019-12-06
> **mauser9069 said:**
> Thank you for clarifying it. I misunderstood the question. [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1853619](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/1853619)

You're welcome and that is OK. Seems launchpad is down at the moment for everyone (see attachment).

When launchpad comes back online your report can be checked out further.

Regards, yeti.

---

### Post by mörgæs on 2019-12-07
Thanks for the bug report but a report for 18.04 has a very little chance of getting attention. 

Are you able to reproduce the problem in the [daily build]("http://cdimage.ubuntu.com/xubuntu/daily-live/current/") of Xubuntu?

---

### Post by gurdenite on 2019-12-07
A workaround might be to install Synaptic Package Manager and use it to do updates manually.
The dialogue/confirmation boxes are much smaller.

---

### Post by mauser9069 on 2019-12-08
> **gurdenite said:**
> A workaround might be to install Synaptic Package Manager and use it to do updates manually.
The dialogue/confirmation boxes are much smaller.

Thank you for that idea. It would be nice if everything would work properly. I will just move it around as I have been doing.

---

### Post by yetimon_64 on 2019-12-18
> **mauser9069 said:**
> Thank you for that idea. It would be nice if everything would work properly. I will just move it around as I have been doing.

You could possibly automatically resize that Software Updater window with "devilspie2". Devilspie2 runs as a daemon in the background and could match that particular window by name with a "lua script" stored in ~/.config/devilspie2. Rather than manually resizing the window every time this may work for you a bit easier after a bit of initial setting up.

Regards, yeti.

---

