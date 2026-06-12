---
title: "How to run a shell script when system boots or resumes from hibernation"
date: 2007-02-19
forum: General Help
---

### Post by rrwo on 2007-02-19
I have a shell script that looks up what network my laptop is on and configures certain defaults (currently just the default printer).  I even posted a tutorial on it, but...

... the script only seems to sporadically run.  I would like the script to run every time the system boots up and resumes.

I tried adding the script using the update-rc tool, but it doesn't seem to run consistently when I restart the system. (That is, it runs every once in a while, just enough to make me think I've fixed it until I try to repeat the settings.)

I tried adding the script as an OnResume line, but again, it does not run consistently.
 
I tried adding it to the /etc/network/interfaces configuration (since it makes decisions based on the network), but it still does not seem to run consistently.

For what it's worth, I'm using Edgy.

---

