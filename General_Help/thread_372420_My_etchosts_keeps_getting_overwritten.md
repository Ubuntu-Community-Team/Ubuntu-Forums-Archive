---
title: "My /etc/hosts keeps getting overwritten"
date: 2007-02-28
forum: General Help
---

### Post by Digital Spaghetti on 2007-02-28
Hey folks,

Loving Ubuntu - but I have an issue.  I have Ubuntu installed on my laptop, which I used on both my home and work WiFi networks.

Whenever I switch between networks (which I seem to have to do manually every time) it seems my /etc/hosts files keep getting overwritten.  I have done *chmod 666* to the file to try stop it being overwritten, but it doesn't seem to have any effect.

Can anyone suggest anything that will stop this, as I keep having to add my aliases every time.

Thanks

---

### Post by PurplePenguin on 2007-02-28
chmod 666 makes it read/write... I think you were after chmod 444 to make it read-only?

Sorry, but other than that, can't help with your problem.  I think if you change it to 444, though, whatever's overwriting it won't be able to anymore. :)

---

### Post by Digital Spaghetti on 2007-02-28
Thanks very much, I'll give it a try when I get home tonight, see if it gets overwritten.

---

### Post by Digital Spaghetti on 2007-03-02
I found out what my problem was.  I was manually writing my /etc/hosts files - but what I needed to go was go to the Hosts tab in Networking and add it there for each profile.  Once I did that, didn't have any more switching problems.

---

