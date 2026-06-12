---
title: "Open Open 2.3 freezing everywhere"
date: 2007-10-21
forum: General Help
---

### Post by bootsbradford on 2007-10-21
I've just started using Open Office 2.3 after upgrading to gutsy last week. At first I wanted to print something but Open Office just froze. Then I discovered that loads of other actions froze it as well. 

What can I do to stop it freezing. I really need to get the Open Office suite working quickly. There has been a suggestion that changing theme might help? How can I do this?

---

### Post by dcstar on 2007-10-21
> **bootsbradford said:**
> I've just started using Open Office 2.3 after upgrading to gutsy last week. At first I wanted to print something but Open Office just froze. Then I discovered that loads of other actions froze it as well. 

What can I do to stop it freezing. I really need to get the Open Office suite working quickly. There has been a suggestion that changing theme might help? How can I do this?

I saw a post earlier today which had some info on this problem, do a search and you should find something.

---

### Post by Maestro23 on 2007-10-21
> **dcstar said:**
> I saw a post earlier today which had some info on this problem, do a search and you should find something.

I saw something as well earlier.  Had something to do with the openoffice.org-gtk package.  Some said after they deleted this, no more freezing issues.

---

### Post by bootsbradford on 2007-10-21
Turns out there's a bug at the moment, whereby if you are running any customised theme in System > Preferences > Appearance, it causes Open Office to freeze. The workaround is to use a theme like Human or Clearlooks.

---

### Post by phyrewall on 2007-10-21
Had the same problem, since I was using the Divinorum GTK 2.0 theme.. Removed openoffice-gtk (openoffice-gnome was uninstalled as well) and the freezing went away.

Unfortunately, so did my slick theme inside Open Office... 

Anyone open a bug report on this yet?

---

### Post by Down8ve on 2007-10-22
Same freeze for me as well.  This is a MAJOR problem!!  Can you imagine how many folks may give up on Ubuntu when they discover they cannot create word processing documents?

I almost rebooted to Windows for good until I found this post. Have you all submitted a bug report?

---

### Post by _Matrix_ on 2007-10-25
I think the freezing is caused when you try using the Thin Ice theme. When I enable this theme and open word and try to make a change to the formatting properties in tools... options open office locks up. 

To fix I simply enable the Human theme which I think is Ubuntu's default theme and the problem goes away.

Hope this helps.

---

### Post by aethralis on 2007-10-25
See this thread: [http://ubuntuforums.org/showthread.php?t=582152](http://ubuntuforums.org/showthread.php?t=582152)

---

### Post by ricardoec on 2007-10-27
No, way, I am using UBUNTU Studio, installed the oO components and it freezes upon starting.... no oO in GUSTY !!

---

### Post by ricardoec on 2007-10-27
This is odd. The problem seems to be with GTK.

I installed the original Ubuntu Studio theme and OO works now.

---

### Post by ricardoec on 2007-10-27
I retract my self. OO does not work at all.

It does start in full screen mode but ther is no way to control the appss . 

Unbelievable. A Linux distroo without an office suite.

---

### Post by ricardoec on 2007-10-27
Disabling GL Desktop, does the job.. OO works like a charm.

This a HP nw7440 2gbmem 256mb video ram. fresh Gusty install.

---

