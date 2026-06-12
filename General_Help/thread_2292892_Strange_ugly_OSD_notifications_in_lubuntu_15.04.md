---
title: "Strange ugly OSD notifications in lubuntu 15.04?"
date: 2015-08-31
forum: General Help
---

### Post by mike353 on 2015-08-31
How do I fix this? It's like someone sliced up the OSD bubble and then arranged the pieces so that the blank parts cover the words. This is on an Acer Aspire One AOD270 netbook. Everything else works almost perfectly, so it is only a minor annoyance....  (L)ubuntu 15.04 runs very well on this netbook: smooth video and sleep. Windows 7 starter (32 bit)  is a total mess. It's like watching network TV compared to PBS!  Ubuntu 15.04 is usable, but too bloated with silly eye candy effects. Why did they do away with Unity-2D?

---

### Post by Dennis N on 2015-08-31
Post a screenshot of this, please. It will allow us to see the problem.

---

### Post by vasa1 on 2015-08-31
[http://askubuntu.com/questions/544715/there-are-lines-in-the-notifications-in-lubuntu-14-10-see-image-below-whats](http://askubuntu.com/questions/544715/there-are-lines-in-the-notifications-in-lubuntu-14-10-see-image-below-whats)

[http://ubuntuforums.org/showthread.php?t=2265820](http://ubuntuforums.org/showthread.php?t=2265820)

[https://bugs.launchpad.net/ubuntu/+source/lubuntu-artwork/+bug/1362555](https://bugs.launchpad.net/ubuntu/+source/lubuntu-artwork/+bug/1362555)

---

### Post by Dennis N on 2015-08-31
That was my guess too. Just proceeding with caution.

---

### Post by Dennis N on 2015-09-01
If this is the correct diagnosis, we discussed this problem with the appearance of the notifications back in this thread:

[http://ubuntuforums.org/showthread.php?t=2279546](http://ubuntuforums.org/showthread.php?t=2279546)

The fix I used is in post #3 of that thread. A fix is supposed to be included in the upcoming 15.10 release. I plan to test the beta and see for myself.

---

### Post by Dennis N on 2015-09-01
I Looked at the Lubuntu 15.10 Beta Live USB and the notification appearance for the default theme is indeed fixed. There are 4 distinct notification themes now that you can choose from. The lxappearance (Customized Look and Feel) won't start (segfault), so I couldn't check some other things I wanted to, and I ended my session with that.

---

### Post by vasa1 on 2015-09-02
> **Dennis N said:**
> If this is the correct diagnosis, we discussed this problem with the appearance of the notifications back in this thread:

[http://ubuntuforums.org/showthread.php?t=227954](http://ubuntuforums.org/showthread.php?t=227954)

The fix I used is in post #3 of that thread. A fix is supposed to be included in the upcoming 15.10 release. I plan to test the beta and see for myself.

I think this is the correct link: [http://ubuntuforums.org/showthread.php?t=2279546](http://ubuntuforums.org/showthread.php?t=2279546)

---

### Post by Dennis N on 2015-09-02
Looking for Era's Font? No idea where I got that thread number. I fixed the link. Thanks for noticing the error.

---

### Post by mike353 on 2015-09-08
That was it:   ```
/usr/share/themes/Lubuntu-default/gtk-2.0/images/panel-bg.png
```   Just had to remove the picture and now notifications look fine.

---

