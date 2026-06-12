---
title: "How To Remove Persistent App Icon from Applications Window?"
date: 2020-03-11
forum: General Help
---

### Post by mogruith2 on 2020-03-11
Within my Ubuntu 18.10 I have in the Show Applications window an icon for OWASP ZAP.

I'd tried it out, then deleted via terminal commands, but as the icon remained I checked via 
dpkg -l and the application was not listed.

To be doubly sure I ran Synaptic Package Manager, again OWASP ZAP not showing.

Yet I'm left with the icon in the Show Applications Window and wondering how this can be removed?

Any help would be most appreciated.

---

### Post by deadflowr on 2020-03-11
First off, 18.10 is very dead at this point, we recommend upgrading/reinstall a clean fresh supported release.

That said, check snap list
```
snap list
```
I see zaproxy is a snap,
if it is a snap use snap remove command to remove it.
(snap packages do not get listed in dpkg/apt/or synaptic)

if not a snap, you can check if you have a .desktop file for it in ~/.local/share/applications.
(This is where user personalized launchers are and any put in here will never be removed when the package is removed)

So I guess you have 3 things you can try or look into, with installing a supported release being the best (and right) choice.

---

### Post by mogruith2 on 2020-03-11
Thanks, my typo...the OS is 18.04 (not 10) 

I will give those a go, I don't have snap installed, but on looking I found it within: 

 ~/.local/share/applications (and a zap.sh in /user/local/bin) really appreciate your help on that.

I removed it within a terminal using:

sudo rm  /usr/share/applications/'OWASP ZAP-0.desktop'

---

### Post by deadflowr on 2020-03-11
If something related is in /usr/local then more likely installed from source, or at the least manually installed.
In which case maybe the .desktop launcher file is in the system-wide directory /usr/share/applications.

---

### Post by mogruith2 on 2020-03-11
Good advice, thanks a lot for helping.

---

