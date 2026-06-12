---
title: "Gnome Version"
date: 2017-05-07
forum: General Help
---

### Post by Robbyx on 2017-05-07
I have run the software updater to be informed I am up to date. From the following I would have assumed I need to install 3.18.5. Have I misunderstood the feedback?


```
test@robins-desktop:~$ apt-cache show gnome-shell | grep Version
Version: 3.18.5-0ubuntu0.2
Version: 3.18.4-0ubuntu3
test@robins-desktop:~$ gnome-terminal --version
GNOME Terminal 3.18.3
test@robins-desktop:~$ 

```

---

### Post by Dennis N on 2017-05-07
apt can see and show newer version, but Ubuntu's phased updates policy may delay your actual update to the newer version through the update manager tool for up to 2 days. Read more here on phased updates:

[https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

---

### Post by Robbyx on 2017-05-07
Thank you. I am a bit muddled by being 2 steps behind rather than just one, perhaps .4 was held back because of problems.

---

