---
title: "Pidgin and ssl - googletalk and msn"
date: 2007-10-18
forum: General Help
---

### Post by seditiousmonkey on 2007-10-18
Hi all,

Since gutsy is released today/tomorrow i think its got to be ok to post this here.  Basically I can't get pidgin (from gutsy repositories)  to work with msn or googletalk.  It complains that there is no SSL support. However, the debugging info says there is SSL support present.  Was the gutsy version packaged without SSL?  In feisty I was using a getdeb version of pidgin which worked flawlessly, and I was even carefull to uninstall it before upgrading to gutsy.

Im not sure is this is related but pidgin also reckons it is 2.0.2 while synaptic tells me 2.2.1 is installed.

Any ideas would be greatly appreciated.

Regards,

Joe

---

### Post by rakesh139 on 2007-10-18
I face the same issue. I recompiled pidgin from source with the following cofigure time option and it worked:
./cofigure --enable-gnutls=yes --enable-nss=yes

Rakesh

---

### Post by madelman on 2007-10-19
I have the same problem. It sucks, if they know that MSN is one of the most popular IM's, why didn't they compile pidgin with SSL support?

This sucks!

Now I need to download  and recompile when I had it working.

---

### Post by madelman on 2007-10-19
Alright, for those Pidgin users this is what I did to fix Pidgin after upgrading to 7.10:

Go to Synaptic and search for SSL then selected: libnss3-dev, libnss3-tools and libnss3-0d (it might be installed already thie one). Then after installing those, search for pidgin and reinstall it, that should do it. 

At least this worked for MSN service. Did not check googletalk.

---

### Post by dmflad on 2007-10-21
Thanks Madelman.  Used synaptic and added the set of lib* files then reinstalled Pidgin. Now Pidgin okay. So far its only issue I've had post gibbon upgrade.

---

### Post by seditiousmonkey on 2007-10-21
my thanks too Madelman. the fix does work for both msn and googletalk.  hooray!

edit: just so i know is the problem we're having somthing to do with our specific isntalls or is pidgin in the repositories not asking for all its dependancies?

---

### Post by justleen on 2008-03-16
Thank you, that (still) works :)


Most packages where already installed, reinstalled those, et voila!

Cheers!

---

