---
title: "How to stop connectiong to http://auckland.ubuntu.com/ ?"
date: 2007-07-01
forum: General Help
---

### Post by TTL on 2007-07-01
Hello,
while surfing over a GPRS connection (paying for online traffic and not for online time) I had to discover that some process did connect to [http://auckland.ubuntu.com/](http://auckland.ubuntu.com/) and produced about 250 KB of traffic - resulting in some cents of extra charges. I guess it were the index files for the reporsity which were downloaded.
I definitly want to prevent that happening again, but I do no know which program is responsible for that. I guess it may be some programs running as cron-job.

Any help?

I already disableled popularity-contest to prevent costly traffic and doing an apt-get update; apt-get upgrade every few days if I am at a location with an ADSL connection. I am using Kubuntu 6.06 LTS.

---

### Post by bonzodog on 2007-07-01
It's the update manager, which starts automatically when you login. Indeed, what it is doing is connecting to the repo and checking for updates. I'm not sure how, (I don't have gnome) but you can disable this service in the auto-start, and it might be possible by bringing it up and tell it not to start automatically.

---

### Post by rapolas on 2007-07-01
I think you can disable it through synaptic, open synaptic, then settings -> repositories, then open updates tab, and uncheck the box: Check for updates;)

---

