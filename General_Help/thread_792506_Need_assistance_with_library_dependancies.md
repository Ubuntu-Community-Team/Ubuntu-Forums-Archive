---
title: "Need assistance with library dependancies"
date: 2008-05-13
forum: General Help
---

### Post by Wyld on 2008-05-13
Howdy all,

I've been looking into trialling Plone 3.1.1 at work, but have run into an issue which I think boils down to use of installed libraries.  Would like some guidance is possible.

My intention is to get Plone 3.1.1 running with LDAP based authentification. I've been struggling with this, and I *think* I've found the issue, as reported in one of the log files.

ImportError: liblber-2.3.so.0: cannot open shared object file: No such file or directory

A quick 'locate' found that my Heron installation is using ..

/usr/lib/liblber-2.4.so.2
/usr/lib/liblber-2.4.so.2.0.3
/usr/lib/liblber.a
/usr/lib/liblber.so

Now, my query is, what are my options from here on in?  Plone itself is working fine (their Unified Installer creates it's own Python 2.4 and everything else), and if I wasn't using LDAP (or AD I guess), then it's a done deal.  But this issue, is something I've not had to deal with before.

Any advice oh gurus?

-- Mark

---

### Post by zenwalker on 2008-05-13
Well the version whatu  have on the system is +1 than what the package needs. I mean u r using 2.4.x rather than 2.3.x. So try to downgrade u r package, but make sure some other program isnt dependent on this lib.

---

### Post by Wyld on 2008-05-13
Would it perhaps be possible to have the 2.3 libraries in a seperate location, specific to plone .. in the same way it uses its own version of python?

Just thinking out loud here .. Plone looks like the perfect solution for me, but without LDAP connectivity, it's just not viable.

---

### Post by zenwalker on 2008-05-13
Yep u can have 2.3.X ver libs on /usr/blah path, but u r installation package shud look there instead of lookng at /usr/lib. So i think u need to modify configure scripts or pass some path as options.

The best way i would look out for is to find an updated package which will work for default libs avail.

---

