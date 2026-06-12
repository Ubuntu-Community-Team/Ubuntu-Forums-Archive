---
title: "Synaptic package manager not working"
date: 2007-02-23
forum: General Help
---

### Post by w00dchaz on 2007-02-23
For the last couple of days, Synaptic has quit working for me. I used it a lot up to that point and it worked fine. Everything seems to work fine till the last step. Then I get an error message saying failed to fetch and could not connect to local host connection refused.

Any ideas? Is it just a matter of a setting that needs to be changed?

---

### Post by louis_nichols on 2007-02-23
Can you post the exact error message? The problem is not a big one and can be easily solved, but we need specifics.

---

### Post by w00dchaz on 2007-02-23
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.6.8-0ubuntu2~edgy1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/u/unrar-nonfree/unrar_3.6.8-0ubuntu2~edgy1_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

---

### Post by w00dchaz on 2007-02-23
That was just an example, BTW. It doesn't work with other programs either.

---

### Post by louis_nichols on 2007-02-23
This looks like you have the localhost set as proxy somewhere. Please go in Synaptic to Settings>Preferences>Network and make sure there is no proxy there. Or, at least, that it's the right onw, if you do need a proxy Then, go to System>Preferences>Network proxy and check this setting too.

---

### Post by w00dchaz on 2007-02-23
It probably is something like that. I had a similar thing happen to an Opera setting about the same time--happened after a power outage. I'll check that when I get home.

---

### Post by w00dchaz on 2007-02-23
Hmm... Both those places say 'direct internet connection.'

---

### Post by w00dchaz on 2007-02-23
It was anon-proxy. I got rid of it and rebooted and that fixed the problem.

---

