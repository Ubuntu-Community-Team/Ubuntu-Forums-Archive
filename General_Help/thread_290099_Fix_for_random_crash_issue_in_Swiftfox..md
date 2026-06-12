---
title: "Fix for random crash issue in Swiftfox."
date: 2006-10-31
forum: General Help
---

### Post by hikaricore on 2006-10-31
Thank you to distortedstar for [his thread on fixing firefox]("http://www.ubuntuforums.org/showthread.php?t=286069").

I wanted to repost this in a seperate thread for people searching for swiftfox instead of firefox.  :)  I take no credit for this solution, only the adaptation.  So here goes:

---

Assuming you're using gnome and
swiftfox is install at /opt/swiftfox

```
sudo gedit /opt/swiftfox/swiftfox
```

@ line 62 replace

```
export MOZ_PIS_API MOZ_PIS_MOZBINDIR MOZ_PIS_SESSION_PID MOZ_PIS_USER_DIR
```

with

```
export MOZ_PIS_API MOZ_PIS_MOZBINDIR MOZ_PIS_SESSION_PID MOZ_PIS_USER_DIR XLIB_SKIP_ARGB_VISUALS=1
```

Save the file and launch swiftfox and goto the dreaded gmail.com (or whatever sites you know to kill firefox/swiftfox dead), after you login you should notice swiftfox does not close for no good reason. :)

Enjoy.

---

