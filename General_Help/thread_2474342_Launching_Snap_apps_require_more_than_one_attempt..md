---
title: "Launching Snap apps require more than one attempt... (fresh 22.04 install)"
date: 2022-04-26
forum: General Help
---

### Post by el-octogono on 2022-04-26
Hi!!

Fresh 22.04 Ubuntu Studio installation... Snap Apps sometimes require more than one launch by clicking the Icon in the App Launcher menu or by typing its name. Launching the app through KRunner works fine... It's a very annoying bug....

---

### Post by QIII on 2022-04-26
This is not about installing or updating the OS.  

Moved to General Help  ...  you are asking for support and not simply making an observation, correct?

---

### Post by GhX6GZMB on 2022-04-26
Stay away from snaps. You'll be happier.

---

### Post by el-octogono on 2022-04-26
> **QIII said:**
> This is not about installing or updating the OS.  

Moved to General Help  ...  you are asking for support and not simply making an observation, correct?

Yes, I'm asking for a solution or hint, or even if it happens to anyone else. However I DO believe it is an Install question, based on what I saw posted on the Install and Upgrade section and that it is a bug that shows as soon as you start using the clean install. I've been using Ubuntu Studio 21.10 with no problems at all and I chose to do a fresh install of the 22.04 LTS, but I'm having a lot of issues... this one is just the most annoying.


> Stay away from snaps. You'll be happier.          

Yes... but if I want to stay away from Snaps I should leave Ubuntu entirely...


Other things that are not working properly are:

- Can't download new Widget: I get the 'Unknown Open Collaboration Service API error. (0)'. I tried googling about this error but none of the proposed solutions worked or made sense...
- Discover: Most of the Plasma Addons show empty except the installed Widgets and Fonts. This didn't happen with U-Studio 21.10.

---

### Post by vanadium on 2022-04-27
It is probably not that you need to click the dock twice, but rather the fact that snap applications can be quite slow to launch the first time you launch them in a session. For example, on a freshly installed Ubuntu desktop right after logging in, it will take several seconds to launch firefox. When you close firefox, then reopen it, the launch is quite a lot faster (though still slightly slower than a DEB or flatpak version)

---

### Post by el-octogono on 2022-04-27
Hi! I'm aware of the Snaps delay. I have an SSD and that delay is barely noticed BUT, this is not the case, the app just won't start at all!!!

In U-Studio when the app is loading the mouse cursor adds a miniature icon. Sometimes the icon doesn't appear, sometimes it appears just an instant.

Just for clarification, I did a full clean install twice, with the same issue replicating and, as I said above, previous 21.10 version worked fine.

---

### Post by el-octogono on 2022-04-27
I found the issue. An instance of Fluidsynth kept running silently in the background. I found it because the Audio Notification panel showed the app!!! System Monitor didn't show Fluidsynth running in the Apps tab but I found it running as a process. I had to Kill it in order to remove it because it resisted other methods... Now apps are launching fine... Hope this helps anyone who may have a similar issue.

---

