---
title: "What ports does apt-get uses?"
date: 2007-06-20
forum: General Help
---

### Post by technomaniac on 2007-06-20
I have this strange problem whenever I try to download software from the repositories through my college internet connection. Synaptic as well as apt-get are unable to contact the repository. Our college server has only 5 ports open on it including the http daemon port. I want to know which ports need to be open for synaptic or apt-get to work. Also can I get them to work through any port.

---

### Post by eZtaR on 2007-06-20
[Here's](http://www.linuxforums.org/forum/installation/1041-apt-get.html) a post discussing your question :)

---

### Post by kuja on 2007-06-20
I think it's port 80 (http), but it's hard to be sure really. That's the conclusion I came to when I setup a firewall a while back anyway, because after setting it up I could still use apt.

---

