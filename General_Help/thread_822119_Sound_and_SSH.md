---
title: "Sound and SSH"
date: 2008-06-07
forum: General Help
---

### Post by lfaraone on 2008-06-07
I'm running Hardy, and I use my OLPC XO (running fedora) to ssh into my primary box. Oddly enough, applications run faster via X11 forwarding and SSH than they do on the lappy.

Is there any easy way to forward sound as well?

Thanks!

---

### Post by unixg33k on 2008-06-08
This can be done with artsd - might take some tweaking.

Start artsd with "artsd -n -u -p 5001" which tells artsd to use networked sound and listen on port 5001.

Configure the machine sending the sound to send to the target machine. Set the environment variable ALSA_SERVER to the target. (ie: export ALSA_SERVER=192.168.0.5:5001).

I've never done this personally, but it's supposed to work - and maybe at least it will send you in the right direction.

---

