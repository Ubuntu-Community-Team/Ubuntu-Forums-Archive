---
title: "GUI lost - wrong kernel?"
date: 2006-12-02
forum: General Help
---

### Post by lolwhites on 2006-12-02
While trying to install an nvidia graphics card (more on that later) using these instructions: [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

When I got to Step 2 of "Install and activate drivers" I must have selected the wrong kernel module, as when I restart, it gets as far as "starting kernel log" before giving me the following message:

"Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

When I select "yes", it gives me a lot of info; I think the relevant parts are:

*(==) Log file: "var/log/Xorg.0.log*and
*(==) Using control file: "/etc/XII/Xorg.conf*
n.b. there is more, I've written it down so just ask if it's necessary

It then lets me log in, but in the non-graphical interface, and I have no idea what to do next!

How can I get my old GUI back?

---

### Post by lamego on 2006-12-02
Login into the terminal and run the text mode xserver configuration utility:
```
sudo dpkg-reconfigure xserver-xorg

```

---

### Post by lolwhites on 2006-12-02
Thanks! Not only do I have my GUI back but it now recognises the card, which it wasn't doing before.

---

### Post by LinuxVox on 2006-12-02
I tried using this utility & still no Xserver! Are there any other options? Should I retry it again by entering the amount of video RAM in kB?

Vox

---

