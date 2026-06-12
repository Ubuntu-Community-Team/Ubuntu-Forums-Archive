---
title: "What has more usable RAM: 32-bit w/ 3GB or 64-bit w/ 4GB?"
date: 2008-03-07
forum: General Help
---

### Post by DeegC on 2008-03-07
I know the answer is highly dependent on what I'm running on my PC but I'm looking for a ballpark idea.

I'm running 32-bit Ubuntu on a MacBook Pro with 4GB of RAM.   Unfortunately it only sees a little over 3GB of RAM.  Hunting around the forums it looks like the only way to see all 4GB is to install 64-bit Ubuntu.  However, a 64-bit programs use more RAM to store the pointers.

My question is "How much more?"  Will I get more usable RAM with 32-bit/3GB or with 64-bit/4GB?  I'm topped out with 4GB so I don't want to take the time to install 64-bit Ubuntu if I end up using more RAM.

Most of my work is done using Java applications (e.g. Eclipse and Squirrel) and running apache/tomcat.  I also have the usual suspects running: terminals, Firefox, Evolution, etc.

Thanks for any insight.

---

### Post by disturbedite on 2008-03-07
there is a question of the benefits of using 32bit or 64bit?  the benefits of using 64bit far outweigh the benefits of using 32bit, i'd think...

---

### Post by kebes on 2008-03-07
This is quite an interesting question. I've never measured it myself, but doing some web searches (e.g. [this]("http://lists.centos.org/pipermail/centos/2006-August/068976.html"), [this]("http://benjchristensen.wordpress.com/2007/02/16/32-bit-versus-64-bit-jdk-memory-usage/"), [this]("http://www.newmobilecomputing.com/story/5768/Are_64-bit_Binaries_Really_Slower_than_32-bit_Binaries_/page3/")) it seems that 64-bit binaries and data structures can be 15% to 40% bigger than their 32-bit counterparts.

In your case, the difference in RAM (~30%) is similar to these differences in RAM usage, so it's not at all obvious which one is better. The only way to know for sure would be to run real tests for the applications you care about.

Seems like the gain in any case would be small. Maybe not worth the effort of reinstalling?

---

### Post by gobbles414 on 2008-03-07
> **DeegC said:**
> I know the answer is highly dependent on what I'm running on my PC but I'm looking for a ballpark idea.

I'm running 32-bit Ubuntu on a MacBook Pro with 4GB of RAM.   Unfortunately it only sees a little over 3GB of RAM.  Hunting around the forums it looks like the only way to see all 4GB is to install 64-bit Ubuntu.  However, a 64-bit programs use more RAM to store the pointers.

My question is "How much more?"  Will I get more usable RAM with 32-bit/3GB or with 64-bit/4GB?  I'm topped out with 4GB so I don't want to take the time to install 64-bit Ubuntu if I end up using more RAM.

Most of my work is done using Java applications (e.g. Eclipse and Squirrel) and running apache/tomcat.  I also have the usual suspects running: terminals, Firefox, Evolution, etc.

Thanks for any insight.

There have been several revisions of the MacBook Pro. The early MacBook Pros were based on the Intel 945 mobile chipset. 945-based laptops cannot address all of your 4 GB of RAM -- even with a 64-bit OS installed. MacBook Pros based on the newer Intel 965 mobile chipset will allow a 64-bit Ubuntu to use 4 GB of RAM. Of course, 32-bit Ubuntu will still be restricted to approximately 3 GB of RAM.

I honestly don't know whether or not 32-bit Ubuntu can use multiple processor cores; 32-bit Windows can't. I'd actually be interested to learn more about this myself. But I do know that there are still some Linux applications that won't run well in 64-bit operating systems. So you should investigate the 64-bit status of all of the programs/plugins that you've been using in 32-bit Ubuntu.

Does any of this help? Please keep me up-to-date with your progress.

---

### Post by pointone on 2008-03-07
Both 32-bit Windows and Linux can use multiple processors.

---

### Post by gobbles414 on 2008-03-07
> **pointone said:**
> Both 32-bit Windows and Linux can use multiple processors.

Thanks for the info.

---

### Post by Nythain on 2008-03-07
the amount of extra ram used, if any (its not a garaunteed increase really), of a 64bit version of a program vs. its 32bit counterpart is very minimal... and when you are talking an extra gig roughly of ram difference between the two set ups, it would take a metric buttload of apps running at once for the small amount of extra ram to accumulate to that extra gig

in a nutshell, in theory, and in my opinion, the 64bit with the almost entire gig of extra ram will have more free ram and ram performance than the 32bit setup

---

