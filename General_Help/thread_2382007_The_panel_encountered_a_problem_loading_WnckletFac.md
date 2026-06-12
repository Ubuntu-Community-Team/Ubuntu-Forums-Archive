---
title: "The panel encountered a problem loading WnckletFactory::WindowListApplet"
date: 2018-01-07
forum: General Help
---

### Post by cscj01 on 2018-01-07
I am running 16.04 x64 with Gnome Flashback.  Today I received the following message:```
The panel encountered a problem loading WnckletFactory::WindowListApplet
Do you want to delete the applet from your configuration?
```I searched and found some entries back in 2010 and 2011.  I am not sure how to correct this problem from those threads.  Can someone give me some guidance here?  Thanks.

Note:  My panel no longer shows running applications.

---

### Post by cruzer001 on 2018-01-07
Yes, there are several old bug reports out on this with no fix, just a couple of work-a-rounds.

[https://bugzilla.gnome.org/show_bug.cgi?id=637219#c6](https://bugzilla.gnome.org/show_bug.cgi?id=637219#c6)

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/716714/comments/17](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/716714/comments/17)

I say that if it hasn't been fixed in 6 years, it not going to be fixed.

---

### Post by cscj01 on 2018-01-07
> **cruzer001 said:**
> Yes, there are several old bug reports out on this with no fix, just a couple of work-a-rounds.

[https://bugzilla.gnome.org/show_bug.cgi?id=637219#c6](https://bugzilla.gnome.org/show_bug.cgi?id=637219#c6)

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/716714/comments/17](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/716714/comments/17)

I say that if it hasn't been fixed in 6 years, it not going to be fixed.

I can use pkill gnome-panel to kill it, but what is the command to restart?  Do I do this in a terminal?
Also, I have 2 panels.  How do I know which one I am killing?

---

### Post by cruzer001 on 2018-01-08
This should do it

[https://www.howtogeek.com/howto/linux/reload-the-gnome-or-kde-panels-without-restarting/](https://www.howtogeek.com/howto/linux/reload-the-gnome-or-kde-panels-without-restarting/)

And both panels will be reset, they are seen as one.

Had an afterthought

You like flashback.  You may also like ubuntuMate.  Its uses gnome2 and works/looks like the old 8.04/10.04 systems.  It uses the newer gtk3, but just maybe a bit more compatible for your needs.

---

