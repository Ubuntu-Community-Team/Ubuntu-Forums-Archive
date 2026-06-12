---
title: "How does Ubuntu pick the mirrors in apt sources.list?"
date: 2006-10-26
forum: General Help
---

### Post by johann_p on 2006-10-26
I am currently running Ubuntu Dapper.
I am located in Austria(Europe) but for some strange reason all the hosts in /etc/apt/sources.list are located in Australia (kangoroos and all that). 

I have no idea why Ubuntu picked those URLs of hosts that are across the globe.

But I would like to change them to closer hosts, ideally in Austria. Is there a way to tell Ubuntu to modify this list to cover a more local area? How can I find out the exact URLs I would need to put in there for Austrian and not Australian hosts.

I want to make this change before I do the upgrade to Edgy.

---

### Post by beerfan on 2006-10-26
This is just a guess but I think Debian is based in Australia and perhaps those mirrors are the only ones which have the appropriate packages at this time. I don't really know if Ubuntu uses debians mirrors or packages or if they have their own though.

---

