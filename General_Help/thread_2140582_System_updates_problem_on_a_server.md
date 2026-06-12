---
title: "System updates problem on a server"
date: 2013-04-30
forum: General Help
---

### Post by Neill_R on 2013-04-30
Hello

I am running 12.04 server with ubuntu-desktop installed on top. Every so often I get errors on startup and they refer to some package that needs updating. 
[INDENT]
Sorry Ubuntu 12.04 has experienced an internal error.
...
Unreportable Reason
You have obsolete packages installed Please upgrade the following packages ...
[/INDENT]

So I 

[INDENT]
sudo apt-get update
sudo apt-get upgrade
[/INDENT]

My question what is happing to cause these packages to become obsolete ( is it just the passage of time and would setting the system clack back a few days make a difference? (i don't think so!)
If it is that somethong has changed, on my system, to cause this error to occur how do (what commands) do I use to examine the  "update"  events

---

### Post by jonobr on 2013-04-30
Hello

I think its depending on the error your getting, it would be nice to see the actual error.

However, when you do the update/upgrade, your machine will go to the repos you have enabled and will check for updates.
It will also notify you of packages that are no longer supported and are either obsolete, deprecated and so on.

It will also install(if you tell it to) replacement packages for certain programs.

When you run the update /upgrade, make sure to look at what it says, it will tell you whats its update, whats broken and whats being removed

Cheers

---

