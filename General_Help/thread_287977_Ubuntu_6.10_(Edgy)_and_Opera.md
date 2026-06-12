---
title: "Ubuntu 6.10 (Edgy) and Opera"
date: 2006-10-29
forum: General Help
---

### Post by JimTDI on 2006-10-29
Hi All!

I don't see Opera listed as a package I can install in Ubuntu 6.10 - although it was there as a package in Dapper.  Is there a repository I need to enable to install it in Edgy?

Thanks!

---

### Post by JimTDI on 2006-10-29
:confused:  Anyone?  No one is running Opera 9.x on Edgy??  Thx again!!

---

### Post by wjp.reg on 2006-10-29
Add this to your /etc/apt/sources.list:

```
deb http://deb.opera.com/opera/ edgy non-free
```

See this site for details: [http://deb.opera.com]("http://deb.opera.com")


cheers!

---

### Post by gyaresu on 2006-10-29
Well they must have changed it in the last hour...
Not there anymore.

I'll try and post back once I've found the answer.

---

### Post by gyaresu on 2006-10-29
Found it.

[http://ubuntuforums.org/showthread.php?t=287460&highlight=opera+edgy](http://ubuntuforums.org/showthread.php?t=287460&highlight=opera+edgy)

> Yeah, it's in the Canonical Commercial repository, along with RealPlayer and some antivirus client. You can add it by putting the following line in your /etc/apt/sources.list file:

Code:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

Yes, that says "dapper." I wasted two hours of my life this morning trying to figure out why the heck Edgy's version wasn't working there - turns out the Packages.gz for Edgy is blank. I suspect the reason for this may have something to do with the fact that no version of Opera for Edgy is out on opera.com yet (although naturally the Dapper version works just fine). I've added the Packages.gz file to my bookmarks to see when it will finally be updated, so until then, I'm just gonna go with the Dapper version.

---

### Post by JimTDI on 2006-10-31
> **wjp.reg said:**
> Add this to your /etc/apt/sources.list:

```
deb http://deb.opera.com/opera/ edgy non-free
```

See this site for details: [http://deb.opera.com]("http://deb.opera.com")


cheers!


Nope... that did NOT allow me to find Opera to install.  But thank you for your reply.  As far as I can see - Opera 9x is not in the commercial Ubuntu repositories, and is not on the Opera site, unless I download the .deb package and install it outside of Synaptic (which I'd prefer not to do at this point).

---

### Post by luxus on 2006-10-31
i install 9.02 with these instructions 
See this site for details: [http://deb.opera.com](http://deb.opera.com)

---

### Post by J.B. Nicholson-Owens on 2006-11-06
I would think not installing Opera is a good thing.

Ubuntu's press release about distributing Opera is confusing at best.  I comment on the cognitive dissonance in [http://www.digitalcitizen.info/2006/07/06/ubuntu-gnulinux-tells-you-who-their-friends-are/](http://www.digitalcitizen.info/2006/07/06/ubuntu-gnulinux-tells-you-who-their-friends-are/) but I'll state it here briefly:

Ubuntu says "Ubuntu will always be free, and will not have restrictive licenses associated with it." yet Opera is licensed so restrictively you are prohibited from giving a copy of Opera to a friend (even non-commercially and verbatim), you are prohibited from inspecting the software so that you cannot see what it might be doing when you run it, and you are prohibited from modifying Opera even to help yourself.

Also confusing is the apparent contradiction with the Ubuntu Philosophy which includes: "people should have the freedom to customise and alter their software in whatever way they see fit." (according to the front page of [http://ubuntulinux.org/](http://ubuntulinux.org/)).

---

