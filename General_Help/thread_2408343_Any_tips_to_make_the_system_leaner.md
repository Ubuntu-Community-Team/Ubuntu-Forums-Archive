---
title: "Any tips to make the system leaner?"
date: 2018-12-17
forum: General Help
---

### Post by tgvbjhknlm on 2018-12-17
I need basic GUI for ease of use, so I did not install the server but the desktop with minimal option. Then I uninstalled some default apps. The system size was about 6GB. 

I thought that was the smallest I could get. But then I found about "Snap". I did not need it on the computer, so I executed, `sudo apt purge snapd ubuntu-core-launcher squashfs-tools`, and it saved about 1GB of storage. Now the system is about 5GB. Are there any other such seldom used features that can be uninstalled to make the system leaner?

---

### Post by HermanAB on 2018-12-17
In my experience, the easiest way to get a lean system is to install a server version and then add a GUI such as XFCE or LXDE to it.

Trying to uninstall stuff is like trying to unscramble an egg.  It is better not to install it in the first place.

The ultimate control over what to install is with Preseeding: [https://www.debian.org/releases/stable/i386/apb.html.en](https://www.debian.org/releases/stable/i386/apb.html.en)

---

