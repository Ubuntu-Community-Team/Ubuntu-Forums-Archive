---
title: "X won't boot until reboot"
date: 2007-01-15
forum: General Help
---

### Post by pihbar on 2007-01-15
I turn on my computer. It gets to X starting, but instead of loading X reports it coudln't start. I go to a different console, login as user, and the terminal prompt never comes up, because after I put in my pass I get spammed by messages about _/dev/null_ (it doesnt exit i think?)

I can log in as root, but _there is no hostname_, and ps -a reveals a few processes, like ps and bash.

i reboot and it starts properly. so probably something from the last session does it. it keeps happening and it will take a while before i notice what is causing the problem. any ideas?

---

### Post by MrJackdaw on 2007-01-17
Have you tired startx from the command prompt? Is there a dodgy line in xorg.conf?

I'm very new to Ubuntu, so these are probably things you have already tried ;)

---

### Post by pihbar on 2007-02-03
hm, i dont think that's it.
when I do dmesg it gives me a bunch of errors from portmap
portmap: rpc call returned 101

---

### Post by pihbar on 2007-02-03
I think this might be the same issue:

[http://www.ubuntuforums.org/showthread.php?t=321760&highlight=portmap+rpc](http://www.ubuntuforums.org/showthread.php?t=321760&highlight=portmap+rpc)

Might, because I find it odd that without having an iptables ruleset I get it blocking somehting... and only sometimes. I'll try and get back to you.

---

