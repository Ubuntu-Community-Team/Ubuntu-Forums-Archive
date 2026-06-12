---
title: "Actual Subversion Packages"
date: 2004-10-14
forum: General Help
---

### Post by Robin Mehner on 2004-10-14
Has anyone a link to current svn-packages? (1.1.0 is current)

I've found a woody apt source for 1.0.8, but if I add it, there's much confusion for apt (like installing an old python-subversion instead of keeping the newer installed).

So, if someone knows where to get a SVN 1.1.0 package, let me know it :)

Thank you in advance.

---

### Post by Robin Mehner on 2004-10-18
So, due the lack of official updates of the repositories I've done a deb Package of Subversion 1.1.0 for myself. I have done it with checkinstall, because dh_make and fakeroot throwing lot of errors.

You can get the package here: [http://www.freak-company.com/deb/subversion_1.1.0_i386.deb](http://www.freak-company.com/deb/subversion_1.1.0_i386.deb)

for more Information about Subversion visit [http://subversion.tigris.org](http://subversion.tigris.org) 

Some things to note:
- It's my very first deb package, it worked for me, but no guarantee that it will work for you
- apt will complain because subversion_tools is not for svn1.1.0. Because I have no use for them, I just removed them, and it worked
- feedback is wanted

---

