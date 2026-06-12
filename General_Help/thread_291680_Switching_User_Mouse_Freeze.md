---
title: "Switching User Mouse Freeze"
date: 2006-11-02
forum: General Help
---

### Post by danish_demon on 2006-11-02
greetings all,

i've been having this problem since i originally installed ubuntu on this laptop last winter (breezy badger).

some times when i switch users the mouse freezes while everything else works.  if i then switch back the mouse comes back, but now with 6.10 every time i switch from my account (an admin account) to another, non-admin, account the mouse freezes and doesn't come back until i get out of that user's account.

any suggestions?  any logs i could post?  i've looked at a few of the logs and haven't found anything of use.

thanks.

---

### Post by Snapper187 on 2006-11-04
I can confirm to this problem and believe that gnome-screensaver is somewhat buggy in edgy: Besides from the issues when I can still see the mouse cursor but it can't be moved, my screen has been locked up completely as well with no sign of a mouse cursor on other occasions.

Think this is worth a bug report, haven't found anything on launchpad.

---

### Post by Snapper187 on 2006-11-04
Well in fact, I've just found a [support request]("https://launchpad.net/products/gnome-screensaver/+ticket/696") instead of a bug report which seems related to or even a duplicate of this bug.

Since the guy didn't know how to report to the GNOME bugzilla, I've taken care of that and [filed the bug]("http://bugzilla.gnome.org/show_bug.cgi?id=370809"). Feel free to add comments as the issue seems to show up in different ways.

---

### Post by ille on 2006-11-12
I can report that I also have had this problem with my touchmousepad. Today I did a clean install of 6.10. and it got worse than in 6.06.

Before 6.10 I could do a CTRL-ALT F6 and CTRL-ALT F7 to get it working but now the mouse is stuck.  

System 
Compaq Presario X1000. 
2 user accounts (one administrator)

---

### Post by paperdiesel on 2006-11-30
Same issue here with a Dell Inspiron E1505 Laptop running Edgy 6.10.  The mouse is totally frozen, but I can usually switch back to the original user with ctrl-alt-backspace.

Any word on a fix?

---

### Post by ille on 2006-12-02
I've moved the gnoome-screensaver so now I can switch user without any problems:

sudo mv /usr/bin/gnome-screensaver /usr/bin/gnome-screensaver.org

---

### Post by 1002285 on 2006-12-02
> **ille said:**
> I've moved the gnoome-screensaver so now I can switch user without any problems:

sudo mv /usr/bin/gnome-screensaver /usr/bin/gnome-screensaver.org

didn't work for me.

---

### Post by rockballad on 2007-08-05
> sudo mv /usr/bin/gnome-screensaver /usr/bin/gnome-screensaver.org

Thanks. It works for me!

---

### Post by patmalcolm91 on 2007-08-07
this didn't work for me either. :(  hopefully this will be fixed in Gutsy

---

