---
title: "NetBeans won't run"
date: 2006-12-31
forum: General Help
---

### Post by Tom B on 2006-12-31
I just upgraded from Dapper to Edgy, and everything has worked fine except NetBeans. When I clicked on the launcher, nothing happened, so I went to a terminal and typed "/home/tommy/netbeans-5.5/bin/netbeans" which gave me "Cannot find java. Please use the --jdkhome switch." Not knowing what that meant, I tried BlueJ, just to see if it would work. Nope. It gave me "/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/bin/java: not found" So I went to Filesystem, and sure enough, no usr folder. There are only three folders: debootstrap, home, and media, and something called usplash_fifo. What did I do, and how can I fix it?

---

### Post by Tom B on 2007-01-01
Okay, so I poked around a little bit. Turns out all the stuff that used to be in my filesystem was now hidden for some reason, so i removed it all from the .hidden file. But now I went through and found that while it was looking for java.bunchofstuff.06, I had java.bunchofstuff.08. I assume moving to edgy updated java, but now how do I make netbeans and bluej use the new version of java? Do I have to re-install or update them?

---

### Post by Tom B on 2007-01-01
Okay, just in case anybody else runs into this or a similar problem- BlueJ needs to be reinstalled when you update your Java SDK, so I just reinstalled it.  I assumed the same was true for NetBeans, and reinstalled it as well. After finding this site, [http://wiki.netbeans.org/wiki/view/FaqJdkHome]("http://wiki.netbeans.org/wiki/view/FaqJdkHome")
I don't think it was necessary. Oh, well, it all works now.

---

