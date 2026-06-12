---
title: "Can't find OpenShot after installing through software center"
date: 2013-12-12
forum: General Help
---

### Post by Vannyi on 2013-12-12
I went into the software center on Ubuntu 12.04 and installed OpenShot Video Editor.

I then clicked on the Dash Home screen and typed in OpenShot and nothing shows up.  I've also looked at the list of installed programs and it does not show.  If I go back into the Software Center, it does show that the application is installed.

Could someone please tell me how do I start this application?

Thank you

---

### Post by claracc on 2013-12-12
I suppose you have tried to look for openshot (no capital letters) in the dash, don't you?

Anycase, you can find the executable openshot in /usr/bin/ directory, opening a xterm, you can also run the video editor in the background from the xterm with the command:

```
openshot &
```

---

### Post by newbie-user on 2013-12-12
In the terminal, try running: 
```
sudo update-desktop-database
```

You could also start Openshot from the command line:
[http://www.openshotusers.com/help/1.3/en/ar01s02.html](http://www.openshotusers.com/help/1.3/en/ar01s02.html)

---

