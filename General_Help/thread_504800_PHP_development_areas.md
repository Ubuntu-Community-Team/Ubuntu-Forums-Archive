---
title: "PHP development areas"
date: 2007-07-19
forum: General Help
---

### Post by eklypse on 2007-07-19
I am a beginner and started with a website development company.  I was curious if there is a way to have apache automatically create a new subdomain "sub.domain.com" if I create a folder "/domain.com/sub"?  We want to create development areas to use for new sites and I don't even know where to start.  We also want some thing easy that doesn't require us to change 50 settings for each project.  Another thing is if there is even a better or smarter way of doing it all suggestions are welcome.

---

### Post by kidders on 2007-07-20
Hi there,

Obviously, Apache needs to be reconfigured & restarted to make it recognise new subdomains. I suggest writing a script to add/remove Apache subdomains quickly.

---

### Post by merkur2k on 2007-07-20
Its really two problems in one..
The first is the domain name itself. For what you want to work, you will need to have a wildcard dns record setup to point to the webserver. I am guessing that dns administration is not part of you job, so you will have to work with whoever administers that.
The second problem is apache, as you suspected. There is a solution for this, its called dynamic virtual hosts. Its been a very long time since i played with it so i dont remember much about it, just what it is called.
That should at least get you started though.

as for a better or smarter way to do things, it is a very good idea to keep development completely seperate from production, ie on a completely different piece of hardware.

---

