---
title: "Can't make Chrome available to all users"
date: 2013-01-01
forum: General Help
---

### Post by rva1945 on 2013-01-01
There are three users in my 12.04 Ubuntu. The three are Administrators. I install Chrome logged as the "main" user, I mean, the user that installed Ubuntu.

No matter if I download the .deb package or run a terminal command, Chrome appears to my user and to another one, but the third one never sees the Chrome icon.

And the terminal icon is missing too for this user, so I can't try running a terminal command to try running Chrome this way.

Which is the problem with this user?

---

### Post by JiuJitsu500 on 2013-01-01
Remove it completely using synaptic, terminal, or however you know how.

Install Chromium from the software center. Functionality is the same, just open-source. A buddy of mine had this problem some months ago and I couldn't figure out why. Once he installed things from the ubuntu repos, it all worked.

And terminal icon? You mean in the dash dash? Try Alt+f2... can the third user run "chrome-browser" or whatever the command is for normal chrome? It's "chromium-browser" for Chromium, so I'm guessing google didn't change a lot here...

---

### Post by rva1945 on 2013-01-01
> **JiuJitsu500 said:**
> Remove it completely using synaptic, terminal, or however you know how.

Install Chromium from the software center. Functionality is the same, just open-source. A buddy of mine had this problem some months ago and I couldn't figure out why. Once he installed things from the ubuntu repos, it all worked.

And terminal icon? You mean in the dash dash? Try Alt+f2... can the third user run "chrome-browser" or whatever the command is for normal chrome? It's "chromium-browser" for Chromium, so I'm guessing google didn't change a lot here...

Having it installed, I tried it in the users' session: ALT+F2 gnome-terminal, luckily it was there, then google-chrome in terminal, then Dash screen, searched for Chrome, and dragged it into the launcher. It worked.

Thanks

---

