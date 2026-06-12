---
title: "Computer Name"
date: 2012-12-15
forum: General Help
---

### Post by N1nj4turtl3 on 2012-12-15
Howdy guys!

I'm trying to figure out what's going on with my computer name. 

When I installed Ubuntu I named my laptop "n1nj4turtl3-ub" (the Windows partition is named "n1nj4turtl3", if relevant).

When I'm connected to my router and I visit the connected devices router page it lists my laptop correctly as "n1nj4turtl3-ub" but when I run an nmap scan or a metasploit infected page and view the log after I visit the page on my laptop, it lists my laptop as "Andy-Laptop". 

The only time I used my name in Ubuntu was for my username, so I'm not sure how it's getting that as the computer name.

I'd like to change it if at all possible so it says "n1nj4turtl3-ub" or something similar.

Running "gedit /etc/hostname" returns the correct name of "n1nj4turtl3-ub".

Any help is appreciated!

---

### Post by zombifier25 on 2012-12-15
Check both the files /etc/hosts and /etc/hostname, see if they're similar.

---

### Post by N1nj4turtl3 on 2012-12-16
Both files show the correct name as "n1nj4turtl3-ub".

---

### Post by steeldriver on 2012-12-16
Is this on a home LAN (using avahi for name services) or a fully qualified DNS setup? 

If the former maybe you have a non-default host-name entry in your avahi-daemon.conf file (which will override the hostname I think)?

---

### Post by N1nj4turtl3 on 2012-12-17
I use google as my DNS if that answers your question.
I opened avahi-daemon.conf and the host-name is "foo", but that line is commented out.

---

### Post by N1nj4turtl3 on 2012-12-20
Does anyone have any ideas?

---

