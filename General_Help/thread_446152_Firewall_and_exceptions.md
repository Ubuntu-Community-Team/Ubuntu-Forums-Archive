---
title: "Firewall and exceptions"
date: 2007-05-16
forum: General Help
---

### Post by foging on 2007-05-16
Hello!

I'm a total newbie running Ubuntu Feisty and I've been fiddling around with mt-daapd to play music through iTunes. I can't seem to get it to work properly, so I've consulted the Firefly user forum. One of the site admins gave me this tip:
"If you got it from the etch repository, then you are fine -- it's using avahi. If it shows up when you start avahi and then goes away after a half hour or so, then it's a firewall issue. I think your feisty box has a built-in firewall. You'll need to add an exception for multicast, but that's a question better asked on the ubuntu forums, I think."

First off, I haven't configured any firewall on my installation, is it on by default? How do I check if have a config as he says and if I do have a firewall, how do I add an exception for multicast?

Any tips?

---

### Post by orb9220 on 2007-05-16
i> Is it on by default? 

Yes it is called iptables and it is configured. The Gui frontend for iptables is called firestarter and is in synaptic.

> how do I add an exception for multicast?

Don't know but others here probably have an answer for you. Just keep checking back here.

---

### Post by zim65 on 2007-05-28
I could not get mt-daapd to work if installed from synaptic . I followed steps from this link, worked fine but installs older mt-daapd and Feisty wants to upgrade it. If you upgrade mt-daapd I could not get it to work.

[http://www.mrblack.co.uk/blog/2007/04/02/tunnelling-music-from-ubuntu-to-itunes-via-ssh/](http://www.mrblack.co.uk/blog/2007/04/02/tunnelling-music-from-ubuntu-to-itunes-via-ssh/)

---

