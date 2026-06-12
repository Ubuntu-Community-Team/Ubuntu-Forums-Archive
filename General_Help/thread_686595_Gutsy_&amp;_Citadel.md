---
title: "Gutsy &amp; Citadel?"
date: 2008-02-03
forum: General Help
---

### Post by flyinraptr on 2008-02-03
Trying out the Citadel Email server on Gutsy ..... had it working perfectly last night.  But this morning everything inbound and out is getting "invalid recipient" error message.  Obviously, I must have changed a setting to break it but haven't figured it out yet. I know this is really a Citadel issue but haven't been able to find much on their site.  Was hoping maybe someone has already come across this.

Thanks -

---

### Post by jethro10 on 2008-05-24
Im getting exactly the same except one account only is working ok!

remaining are as you get.

did you get it sorted?

Jeff

---

### Post by jethro10 on 2008-06-02
Well, I'm fixed using this info [http://osdir.com/ml/cms.citadel.user/2007-06/msg00020.html](http://osdir.com/ml/cms.citadel.user/2007-06/msg00020.html)

Basically I confused node name for domain name, so Ichanged it to something like "NodeOne"

Then deleted users, re-created them.

Next, re-initialised gloabal address book, from an ubuntu command line, type :-
sendcommand "IGAB"

Works great now. Easy to install by their repo's or downloading a bunch of debs, and now, easy to setup and administer.

Jeff

---

