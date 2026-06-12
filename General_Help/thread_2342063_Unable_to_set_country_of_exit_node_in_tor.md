---
title: "Unable to set country of exit node in tor?"
date: 2016-11-03
forum: General Help
---

### Post by eezacque on 2016-11-03
I have tried to make TOR select an exit node in The Netherlands by adding the following two lines to /etc/tor/torrc:
ExitNodes {NL}
StrictNodes 1


I restarted the TOR service, but TOR still seems to select random exit nodes.

Any clue?

---

### Post by eezacque on 2016-11-11
I just learnt that the Tor Browser has its own torrc in <tor browser folder>/Browser/TorBrowser/Data/Tor.
Setting the exit node there is the way to go.

---

