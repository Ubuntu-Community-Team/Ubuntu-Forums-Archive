---
title: "Ubuntu Software center won't start"
date: 2023-01-01
forum: General Help
---

### Post by maxleod on 2023-01-01
Ubuntu 20.04

I click it, it seems like it's trying to start, then nothing happens. No error message, no nothing.

---

### Post by #&amp;thj^% on 2023-01-01
Will you try this please, and post back any errors:
```
sudo apt-get --purge --reinstall install gnome-software
```
If that don't work next be sure to follow this, Close and Re-launch Ubuntu Software Center

First, if you have the apps opened, close them.

Now you need to terminate the software center processes. To do so, type in the following command.
```
killall snap-store
```
next:
```
killall gnome-software
```
Now any better?

---

### Post by maxleod on 2023-01-01
> **1fallen said:**
> Will you try this please, and post back any errors:
```
sudo apt-get --purge --reinstall install gnome-software
```

Now any better?

Yes, thank you, it's working now. One question though, it's a fresh installation of Ubuntu 20.04, everything up to date, why wasn't something like that working out of the box in the first place?
.

---

### Post by #&amp;thj^% on 2023-01-01
I'm just a volunteer/tester here, You would have to direct that to the Devs for a real definitive reply.
But your in good shape now.

---

### Post by QIII on 2023-01-01
You have had a frustrating experience.  But remember that it is not logical to assume that your experience reflects the general case.  Something caused this to misbehave for you, but for your one instance there may be millions of cases where the issue did not appear.

Don't rush to assume the devs did something wrong.

---

