---
title: "SOLVED: Cannot register additional URL handlers (for SIP)"
date: 2013-01-30
forum: General Help
---

### Post by scotty64 on 2013-01-30
I am using XUbuntu 12.04 and I want to register an additional URL handler that starts my preferred softphone (jitsi) from Thunderbird. There are a couple of extensions that promise that, but they all need a proper URL handler configured. However I tried all kinds of tricks (registering a new handler via gconf, editing thunderbirds configuration etc.), but I always get an "unregistered protocol" error. BTW: Gnome services are running.
Thanks a lot for any advice.

**How to solve it:**

I could solve the problem by editing /usr/share/applications/defaults.list and adding the following line:
x-scheme-handler/sip=jitsi.desktop
This will start Jitsi when a SIP:// URL is called.

However there is a bug in the default Jitsi 2.0 Installations jitsi.desktop file that does not allow passing URLs to jitsi. This can be fixed easily as well:
sudo nano  /usr/share/applications/jitsi.desktop 
Now add %u to the Exed-jitsi line so that it reads:
Exec=jitsi %u

that will do it!

---

### Post by shiraz dindar on 2013-06-12
This totally saved me a lot of hassle. Thank you Scotty!

I too needed to do both steps. 

Ubuntu 13.04, Telify 1.3.3 (firefox add on),  Jitsi 2.2

- Shiraz

---

