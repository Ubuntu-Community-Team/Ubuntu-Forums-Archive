---
title: "Cannot logout of 8.04 without freezing"
date: 2008-05-04
forum: General Help
---

### Post by Support the 2nd on 2008-05-04
I upgraded to 8.04 from 7.10 and now I cannot logout to shutdown my computer without it freezing to a blank screen.

---

### Post by macaholic on 2008-05-04
What kind of graphics card do you have?, it might be a driver issue.

---

### Post by Support the 2nd on 2008-05-04
Ati 9600xt

---

### Post by magnusbb on 2008-05-04
I can confirm this here, also with an ATI card. I guess this is a driver problem.

---

### Post by CryptSphinx on 2008-05-04
Might I direct you to here [https://bugs.launchpad.net/ubuntu/+bug/211318]("https://bugs.launchpad.net/ubuntu/+bug/211318")

This fix didn't work for me (im going to have to keep digging)
but it may help you

(Ati X1300)
(FGLRX - the bane of my existence)

will repost as I find more info

---

### Post by Support the 2nd on 2008-05-05
> **CryptSphinx said:**
> Might I direct you to here [https://bugs.launchpad.net/ubuntu/+bug/211318]("https://bugs.launchpad.net/ubuntu/+bug/211318")

This fix didn't work for me (im going to have to keep digging)
but it may help you

(Ati X1300)
(FGLRX - the bane of my existence)

will repost as I find more info


I checked out that link.  The path that it says to change is a bit different, but I am not familiar enough with linux to know exactly if it matters.

Here is what is post says:
> 

Seems to be a duplicate bug of [https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/181343](https://bugs.launchpad.net/ubuntu/+source/kdebase/+bug/181343) where a fix ([http://ati.cchtml.com/show_bug.cgi?id=992#c26](http://ati.cchtml.com/show_bug.cgi?id=992#c26)) is posted, included here for quickness:

**In /etc/ati/authatieventsd.sh** locate XDM_AUTH_MASK variable and ensure it is set as:

**XDM_AUTH_MASK=/var/run/xauth/A$1***


Mine is:
 XDM_AUTH_MASK=/var/lib/xdm/authdir/authfiles/A$1*

I will back up my important stuff tomorrow before screwing with it.

---

