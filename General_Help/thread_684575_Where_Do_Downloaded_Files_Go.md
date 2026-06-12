---
title: "Where Do Downloaded Files Go?"
date: 2008-02-01
forum: General Help
---

### Post by matey3 on 2008-02-01
Hello every1;

I was wondering if anyone knew where the (auto) downloaded files go after they have been used by the OS?
I mean I have apt-get install-ed few apps in which the os goes up to the Net and grabs some necessary files and puts them in the local machine to use but then Id like to know if there is certain place these files go?
Or does that depend ? (On what kinda files?) or does Ubuntu Server 7x deletes them afterwards? or?

I appreciate your replies in advance!

Regards;


OK If you want to know why?
I also did a wget and got few new files but I cant install them correctly. I have a feeling that the OS is looking in certain places for these files and not where I manually downloaded them...
thanks!
an old newbee ;-)

---

### Post by taurus on 2008-02-01
If you use Add/Remove, synaptic, apt-get/aptitude, it saves a copy in /var/cache/apt/archives.

What are you trying to build from source and what is the exact error message?

---

