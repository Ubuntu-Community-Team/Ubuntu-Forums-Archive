---
title: "firefox reports wrong version of flash player"
date: 2008-03-23
forum: General Help
---

### Post by moshuptrail on 2008-03-23
For some reason Firefox is reporting its version of Flash Player as an older version:
Example:
> The Player requires version 8 or higher of the Adobe Flash Player. You currently have version: 7.0.68 installed.
In fact, I have carefully followed the instructions to install Flash Player 9 from the repos.
I've checked the files located at /usr/lib/firefox/plugins, and /etc/alternatives, and /usr/lib.  All have been updated.  (I used the manual method from the command line using apt-get to first remove the old version and then install the current version.  I got version 9.0.48\)

So what's up with that?    Could I have a spurious entry in about:config?

---

### Post by moshuptrail on 2008-03-23
Okay, it's Easter morning so I didn't expect much response.
But I think I figured this out:

1. in browser URL line type in about: plugins
this gave me a list of plugins in which Shockwave Player was listed twice
The first entry was the older 7.0.68 and indicated it was located in a .mozilla/plugins sub-directory from my home directory.  (probably something of my own doing)

2. Opened a terminal window and cd'd to that directory and deleted the related files.  In my case it was the only file there.  

3. Restarted Firefox.  Good to go!

---

