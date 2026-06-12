---
title: "KDE supposedly installed, but Gnome still loading"
date: 2005-10-22
forum: General Help
---

### Post by Johanka on 2005-10-22
I've just installed KDE on Ubuntu (previous attempt at installing the latest Kubuntu failed miserably, I couldn't get past the login screen...), following the guidelines on [this wiki page]("https://wiki.ubuntu.com/InstallingKDE"). At some point it asked me to choose between the two desktops, I chose KDE. Alas, now I have the KDE login screen to enter my pwd and then loads Gnome... So I'm somewhere halfway between the two. When I want to shut down, I have to first logout from Gnome and then shutdown from KDE login screen... Sucks major. :(

I'm still pretty new to Linux, no wonder I'm stuck.

How can I enable KDE in full?

---

### Post by Staesys on 2005-10-22
This has to be the strangest problem I've heard of yet. Have you tried uninstalling gnome?

Why did your Kubuntu install fail? I had some issues with x.org on mine, but once I loaded the ATI fglrx drivers and ran the config I booted into the GUI nicely.

---

### Post by Johanka on 2005-10-22
Kubuntu installed but the password didn't work, only in text mode and then I was unable to shutdown in text mode. :( So, I decided to go via Ubuntu.

How do I switch the desktop manager back to Gnome?

---

### Post by Staesys on 2005-10-22
The simple answer is to remove anything KDE through Synaptic. From my experience, that should do it.

---

### Post by Johanka on 2005-10-22
But I can't remove everything KDE because Gnome run **inside** KDE. I tried "sudo apt-get remove ubuntu-desktop", but it's still there and loads inside KDE.

---

### Post by xequence on 2005-10-22
Well, in GDM I click "session" and I can choose what I use. (Gnome, KDE, and my other DEs I have)

---

### Post by Johanka on 2005-10-22
Thanks for your input, guys.
I've now managed to wipe out KDE successfully. But this is not where I want to be... Time to look for a different, more KDE-centric flavour of Linux I guess. :rolleyes:

---

### Post by Staesys on 2005-10-22
I'd try one more install with Kubuntu. Perhaps from a freshly downloaded ISO?

I didn't have the problems you described, just a mix up with the x.org configuration, and that was only because it got confused between my onboard video and the ATI Radeon 9250 card I have installed.

---

### Post by Seth on 2005-10-22
What you did was choose between KDM and GDM, the login managers. However, after you switch to KDM, **then** you have to click the Sessions menu and choose KDE. You just didn't do that extra step.

I had both Gnome and KDE installed, and used KDM (KDE Login Manager). I could boot to either Gnome or KDE.

Give it one more try :)

---

### Post by Sirin on 2005-10-22
[QUOTE=Johanka]When I want to shut down, I have to first logout from Gnome and then shutdown from KDE login screen... Sucks major. :([/QUOTE]

The reason you cannot directly shutdown or restart from Gnome when KDM is because KDM was built for KDE, so Gnome can't take superior advantage of it like KDE can (but that doesn't mean it'll screw GNOME up ;)). The same is with KDE if you install GDM and select it as the default Display Manager (DM). 
:D

---

