---
title: "Gnupg2"
date: 2015-03-20
forum: General Help
---

### Post by cathect2 on 2015-03-20
So, it seems that Ubuntu comes with GnuPG. My Enigmail that I use with Thunderbird is now telling me that it will only use GnuPG2 in future versions. My question is what I should do here. Since GnuPG seems to be an essential program in Ubuntu, I don't think I can uninstall it without blowing up the OS. But can I just install GnuPG2 beside it and rock on? 

Anyone delt with this before?

---

### Post by deadflowr on 2015-03-20
You can/should be able to install both.
From the manpages
> In contrast to the standalone version gpg, which  is  more  suited  for
       server and embedded platforms, this version is installed under the name
       gpg2 and more targeted to the desktop  as  it  requires  several  other
       modules   to  be  installed.   The  standalone  version  will  be  kept
       maintained and it is possible to install  both  versions  on  the  same
       system.   If  you need to use different configuration files, you should
       make use of something like &#8216;gpg.conf-2&#8217; instead of just &#8216;gpg.conf&#8217;.

ManPage: [http://manpages.ubuntu.com/manpages/lucid/man1/gpg2.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/gpg2.1.html)

---

