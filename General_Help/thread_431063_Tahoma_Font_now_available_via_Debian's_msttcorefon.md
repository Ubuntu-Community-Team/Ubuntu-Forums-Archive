---
title: "Tahoma Font now available via Debian's msttcorefonts package"
date: 2007-05-02
forum: General Help
---

### Post by Limulus on 2007-05-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/50529](https://bugs.launchpad.net/ubuntu/+source/msttcorefonts/+bug/50529) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				To all those who need the Tahoma font, I just noticed that its now available via Debian's msttcorefonts package, which works on my Feisty install.  Here's how to get it:

1. go to [http://packages.debian.org/unstable/x11/msttcorefonts](http://packages.debian.org/unstable/x11/msttcorefonts) and scroll down to the "Download msttcorefonts" area and click the "all" (Architectures) link.  Download the DEB file from one of the mirrors.

2. double-click the DEB to run Gdebi to install it.  You'll need to input your password.

That should be it :)  Enjoy!

---

### Post by bekirserifoglu on 2007-05-14
thanks man. it works great!!!

---

### Post by peyote on 2007-05-14
msttcorefonts only installs one half of the tahoma font. tahomabd.ttf is not getting installed (only tahoma.ttf).
As a result  websites in Firefox look really bad if they use tahoma
bold (washed out).

---

### Post by tkinkhorst on 2007-05-17
We take the font from a Microsoft supplied .cab file. This file does not contain the bold variant as far as I know.


The problem is hence that we cannot just install the bold font, since there's no free distribution of that available. If we leave Tahoma out completely, that would of course mean that the "regular" tahoma is also not available anymore.

I'm open to suggestions on this matter.



Thijs
(msttcorefonts maintainer)

---

### Post by tkinkhorst on 2007-05-19
The tahoma font will be removed from msttcorefonts 2.1, because it seems to cause more problems than it solves.

---

### Post by bekirserifoglu on 2007-06-06
ya tahoma has been removed from the msttcorefonts but you can still have it. 

[http://ubuntuforums.org/archive/index.php/t-82318.html](http://ubuntuforums.org/archive/index.php/t-82318.html)

This link helped everybody including me. and it works great.

---

