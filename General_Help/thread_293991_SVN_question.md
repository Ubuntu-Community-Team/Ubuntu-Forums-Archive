---
title: "SVN question"
date: 2006-11-06
forum: General Help
---

### Post by Cable on 2006-11-06
A friend of mine is wanting to set up SVN on an Ubuntu box at his house as he and some friends are planning to develop a game together.  He has asked me to help him set it up, and I'm completely new to it.  So bear with me here.

I'm sort of confused about setting up access to the repository.  If I set it up using the custom SVN protocol, will the other guys working on the project be able to access it from their home computers?  As in...could he just forward some ports on his router and have it work perfectly fine if they connect to his IP, or does he need to have a domain/set up apache?

Those are the only two questions I can think of at the moment.  Any other hints about getting this set up would be appreciated.

---

### Post by Cable on 2006-11-06
Bump.

---

### Post by sebastfr on 2006-11-06
> **Cable said:**
> A friend of mine is wanting to set up SVN on an Ubuntu box at his house as he and some friends are planning to develop a game together.  He has asked me to help him set it up, and I'm completely new to it.  So bear with me here.

I'm sort of confused about setting up access to the repository.  If I set it up using the custom SVN protocol, will the other guys working on the project be able to access it from their home computers?  As in...could he just forward some ports on his router and have it work perfectly fine if they connect to his IP, or does he need to have a domain/set up apache?

Those are the only two questions I can think of at the moment.  Any other hints about getting this set up would be appreciated.

hiya

Short answer: it should work with port forwarding enabled on the router (that is port 3690 tcp and udp) and people using the router's IP to connect to.

Apache is not necessary as far as I know unless you want to be able to browse the SVN tree from a web browser.

seb

---

