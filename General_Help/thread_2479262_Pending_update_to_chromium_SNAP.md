---
title: "Pending update to chromium SNAP"
date: 2022-09-19
forum: General Help
---

### Post by Tom_Carr on 2022-09-19
I got a message that says "Pending update to chromium SNAP, close the app to avoid disruptions"

What exactly does this mean and what am I supposed to do?  Just close chromium and reopen it?

---

### Post by ian-weisser on 2022-09-19
Snaps cannot currently be updated while they are running. Hence the notification when an available update is detected.

You have three options:

If --for whatever reason-- Chromium is not running the next time that snapd checks (about 4 times daily), then the system will silently update the Chromium snap. The next time you launch Chromium, it will be the fresh newly-updated Chromium.

If Chromium is running when snapd checks for updates, you get the notification. If the countdown  reaches zero, then the system will terminate your Chromium session  (losing all unsaved work). The system will spend about 60 seconds  updating the Chromium snap, then you can reopen your fresh newly-updated  Chromium.

If you tire of the notification, you can update immediately:

- Quit out of Chromium
- Run "sudo snap refresh"
- Wait for the command to complete
- Launch your fresh, newly-updated Chromium.

---

### Post by grahammechanical on 2022-09-20
This message appears also for the Firefox snap and recently I started getting it for Ubuntu Software (A.K.A. Snap Store).  It is an advance notice and appears even if that particular application is not loaded. When I try to refresh (update) the particular snap app through the terminal I get a message saying that there is no update available. Or something like that. I forget what it is.

It seems to me that a decision has been taken to automatically update/refresh snap applications (or certain ones of them). It removes a dependency on the user to keep this part of the OS up to date. 

It is all part of the rich tapestry of Ubuntu life.

Regards

---

### Post by ian-weisser on 2022-09-20
> **grahammechanical said:**
> appears even if that particular application is not loaded

Try "snap refresh <snap-name>" to find the PID of the blocking process so you can terminate it.

For example, Ubuntu Software (snap-store) remains running even if all windows are closed. (That's why many folks encounter this and get puzzled)

So, using the Ubuntu Software example,

```

snap-store --quit
sudo snap refresh

```

If you get a notification that snap application XYZ, from the snap named "xyz-snap", is still running,

```

sudo snap refresh xyz-snap
  snap xyz-snap has process 12345 
kill 12345
sudo snap refresh

```

---

### Post by Quarkrad on 2023-02-01
This seems plane ridiculous - I have a neighbour I look after (in terms of her pc). I have converted her to ubuntu  and was looking at changing her to snap Chrome so that she did not keep getting messages about updating chrome that she finds annoying and unsettling.  Like it or not she has her pc on for hours working within the google environment; for elderly people who 'just want to work' and 'do not like or want to understand' message pop-ups this is going to crash their workflow while they are in the middle of using it!  I guess I'm going to have to look at putting her back on Windows - for all it's features at least Windows does not, by design, crash whatever you are doing.  If this is true I really cannot believe this got through any form of *customer acceptability* assessment.

---

### Post by BBQdave on 2023-02-02
> **ian-weisser said:**
> If you tire of the notification, you can update immediately:

- Quit out of Chromium
- Run "sudo snap refresh"
- Wait for the command to complete
- Launch your fresh, newly-updated Chromium.
Hi ian-weisser, checking to see if I understand updating Ubuntu 22.04LTS.

From terminal, I use *apt* to update system, and I use *snap* to update applications. Or from GUI: I use **Software Updater** to update system and **Ubuntu Software** (snap) to update applications.


So separate repos for system and applications. And separate command structures to update from those repos, as in *apt* and *snap*? Thanks :)

---

