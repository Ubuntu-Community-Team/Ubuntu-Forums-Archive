---
title: "freetalk"
date: 2007-02-14
forum: General Help
---

### Post by richard42 on 2007-02-14
I'm trying to get freetalk to work with my gtalk login. Does anyone have any experience of this?
I've found that it comes up with a connection error after it has been logged on for a few minutes. However, I've noticed that there is a newer version of freetalk than the one in the Ubuntu repositories, which makes me wonder if that would work better. Unfortunately, I can't get it to build from source on my machine because I get an error about it not being able to use readline.
Has anyone else got this working before who could point me in the right direction?
Alternatively, if anyone knows an alternative jabber console client that works with gtalk then that would work fine as well.
Thanks for your help.
Richard

---

### Post by kungfoofool on 2008-02-07
I updated to the 3.x version of freetalk and still have problems staying connect to gTalk. I think it's some sort of keep-alive issue - if I'm idle for a length of time, I have to /restart. Otherwise, it works fine.

I updated to 3.x by using the debian unstable repository ( [http://packages.debian.org/unstable/](http://packages.debian.org/unstable/) ) and apt-get. After updating, remove the debian repository from /etc/apt/sources.list to keep from installing all sorts of other unnecessary/unwanted updates.

---

