---
title: "Ubuntu 18.04 Server - Glassfish 4"
date: 2019-01-07
forum: General Help
---

### Post by pelgrim on 2019-01-07
Hi,

I struggled for a long time getting my ubuntu server act as a proper router.
In that process I also performed a software update (apt-get update), something I didn't to since the initial install half a year ago.

Right now I can't get glassfish to function anymore.
As a test, I completely purged all java versions, installed new one, but the result is still the same.
Symptoms:
asadmin starts the domain, and while it is doing it's startup process, my web pages are available.
As soon as all is done, I get the message that starting the domain was a success, only to see that the process stops, as if there was a kill command.

I tested with a fresh glassfish as well, just to make sure no error slipped in the config files of my installation.
Working with glassfish for so many years, I know for sure nothing is wrong there.

The only logical conclusion I can draw for now is that something in the ubuntu update must have changed something that makes glassfish crash.
The things I changed manually while fiddling on my router problem were network settings in various config files and ufw.

On my development pc's the same configuration runs glassfish without problems.
Any suggestions are welcome.

---

