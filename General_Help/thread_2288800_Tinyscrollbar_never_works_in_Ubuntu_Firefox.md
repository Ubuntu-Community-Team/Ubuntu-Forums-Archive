---
title: "Tinyscrollbar never works in Ubuntu Firefox?"
date: 2015-07-30
forum: General Help
---

### Post by NoBugs! on 2015-07-30
This is a fairly common libray, and I'm surprised it doesn't work on 14.04 (at least on my 14.04 install): [http://baijs.com/tinyscrollbar/](http://baijs.com/tinyscrollbar/)

Go to the demos and click-and-drag the bubbly scrollbar, it doesn't work. Mousewheel works though. I filed a bug: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1477815](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1477815)

---

### Post by NathanRodriguez on 2015-07-30
Must be some detail on your install, it works correctly here on my 14.04.

---

### Post by NoBugs! on 2015-08-18
No, I mean if you *click *the scrollbar, not using the scrollwheel. It never works in Firefox, and it's a common problem with Firefox and Bootstrap, as well as Tinyscroll. See the last comment on [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1477815](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/1477815).

---

### Post by NoBugs! on 2015-08-20
Here's something interesting, after upgrading from the original 14.04 3.13 to the new 14.04 3.19 it seems this is fixed.

What kernel were you using when dragging scrollbar worked for you?

---

