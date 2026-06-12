---
title: "[SOLVED] ufw default policy"
date: 2008-06-29
forum: General Help
---

### Post by bryncoles on 2008-06-29
hiya people! im just wanting some advice on fiewwalls. i would like to set ufw to drop incoming contacts by default. but im not very bright - so between man ufw, and [https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall), i think its a simple matter of typing 

```
sudo ufw default deny
```

i would like to know is this right? and what are the rammifications of my doing this. will i still be able to brows the web with firefox, or will i accidentally cut myself off? if i accidentally cut myself off, will i have to give ufw specific instructions to allow firefox to connect to the web, then specific instructions to allow update manager to connect, and to allow synaptic, and so forth. and then if i do, how do i do that?

at the moment, ive got the firewall enabled, but its default policies are all accept (am i right), so enabling it is a little pointless. 

oh - and im not using samba, nor wine, nor anything else like that. i would just like to know how to configure the firewall to aggressively block internet connections, while at the same time letting me choose who gets in or out. 

hope its clear what i want to achieve!

thanks to anyone who's reading this!

;-)

---

### Post by brian_p on 2008-06-29
> **bryncoles said:**
> oh - and im not using samba, nor wine, nor anything else like that. i would just like to know how to configure the firewall to aggressively block internet connections, while at the same time letting me choose who gets in or out. 

hope its clear what i want to achieve!

You have already made a choice. You are running no programs (samba, mail server, web server etc) which can allow a connection to your machine from outside. A firewall is not needed.

Unless you have in mind blocking some outgoing connections (for example, requests to websites beginning with the letter 'g') you still do not need a firewall.

Conclusion: uninstall ufw; it is doing nothing for you.

---

### Post by bryncoles on 2008-06-29
that's good to know actually, ta! im wanting to learn a little about how it works though, because who knows, one day i might want to install a service which will listen at some port or other... everything ive found through google just seems a little.... incomprehensible to me. im glad its an UNcomplicated firewall! i dont know what id do if it was difficult ;-)

though its reassuring to know having it or not isnt hurting me either way.

---

