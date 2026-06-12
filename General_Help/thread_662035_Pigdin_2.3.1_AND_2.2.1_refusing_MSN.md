---
title: "Pigdin 2.3.1 AND 2.2.1 refusing MSN"
date: 2008-01-08
forum: General Help
---

### Post by RasmusB on 2008-01-08
Hello!

I made a posting about the problem[ here]("http://ubuntuforums.org/showpost.php?p=4096066&postcount=49") , but i thought i might have a better chance of getting help by starting a separate thread.

I had the standarg pidgin client installed (running gutsy), version 2.2.1. Worked perfectly, but I wanted to upgrade anyway... So I removed my install, installed the packages from getdeb, and it couldn't connect to MSN anymore... ICQ worked though.

Anyways, I uninstalled pidgin again and tried rolling back to the 2.2.1 that can be found in the ubuntu sources... but now that version cant connect either! The reason given is

"Unable to authenticate: Unable to connect"

which doesn't really tell me much... The wierd part is that 2.2.1 was running perfectly, but somehow I managed to break something while installing 2.3.1, which can't be unbroken by rolling back,,,

Any suggestions on how to get *any* version running again? I have tried clearing the .libpurple folder between installations, doesen't help.

---

### Post by akadruid on 2008-07-07
Try deleting just the passport.com and live.com certificates from ~/.purple/certificates/x509/tls_peers.  Even after a clean install these might be the problem.

---

