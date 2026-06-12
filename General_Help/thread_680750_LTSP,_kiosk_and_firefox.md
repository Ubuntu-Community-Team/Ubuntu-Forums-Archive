---
title: "LTSP, kiosk and firefox"
date: 2008-01-28
forum: General Help
---

### Post by RafalW on 2008-01-28
I have installed LTSP on Ubuntu 7.10 Server. I have built thin client environment by 'ltsp-build-client --kiosk'.
Everything works perfect except starting firefox in fullscreen mode(it seems that /opt/ltsp/i386/home/kiosk/.xsession is not read during starting x session).
But the worse thing is that I have no idea how to setup a start page for firefox. I was trying to edit:
/opt/ltsp/i386/etc/firefox/pref/firefox.js
/opt/ltsp/i386/usr/share/firefox/defaults/pref/firefox.js

with
pref("browser.startup.homepage", "http://myfavoritepage.org");

but it doesn't work for me:(
Any changes in .xsession file doesn't affect anything as well.

Anyone has an idea how the firefox is started and where I can setup start page? Thanks in advance.

-- 
Rafal

---

### Post by fredsnet on 2008-01-28
I have no experience with this but wouldn't you setup the home page in firefox as you would   in a normal mode of using firefox.  Doesn't Ltsp just image a copy of the firefox application to each client from your server ?

Rick

---

### Post by RafalW on 2008-01-29
Unfortunately no. Firefox (as a default for ltsp-build-client --kiosk) is installed only in the chroot (/opt/ltsp/i386/) environment for 'kiosk' user. Any changes made from firefox working in the chroot  doesn't persist after reboot.

-- 
RaW

---

### Post by RafalW on 2008-01-29
After spending a long while ;) looking for a solution - found it.

What I did was add:
```
browser.startup.homepage=http://myhomepage
browser.startup.homepage_reset=http://myhomepage
```
into:
  ```
/opt/ltsp/i386/usr/share/firefox/browserconfig.properties
```

and then:
```
ltsp-update-image
```

and then it works!!! But only for PXE bootable clients.
Now I have to find how to update nbi, but this is the subject for another post ;)

-- 
RaW

---

### Post by fredsnet on 2008-01-30
Rafal,

I'm glad you figured it out. I am adding these steps to my LTSP setup notes.  There is far to little information available on this subject.  At some point perhaps we can create a dedicated forum section to LTSP to record all the mods and changes that have accurred.   

Rick

---

