---
title: "Firefox 2.0 Tab Bug"
date: 2006-10-31
forum: General Help
---

### Post by antibiotek on 2006-10-31
Looks like Edgy version of Firefox 2.0 has a bug with tabs.  When you set the option to open new windows in tabs it doesn't work!  I still have new windows popping up rather then tabs. ](*,)

---

### Post by AJRoberts on 2006-10-31
I noticed this as well, and I figured I had just misconfigured something.  I'm using Opera until I can figure it out.

---

### Post by kaamos on 2006-10-31
about:config

browser.link.open_newwindow: 3
browser.link.open_newwindow.restriction: 0

---

### Post by antibiotek on 2006-10-31
thanks, i'll try it when i get home.

it's still a bug in firefox 2 though, where should it get reported?

---

### Post by dskloet on 2006-11-02
Another Tab problem in Firefox 2.0:
I like to open the URL in my mouse buffer by middle clicking but setting middlemouse.contentLoadURL to true doesn't work. Middle clicking on the page does nothing and middle clicking on the tab closes it (which is highly annoying).

---

### Post by loko on 2006-11-02
i realized this bug a few days ago, it is not an edgy-bug, also it has nothing to do with misconfiguration that you have done.

it is a firefox bug.

you can reproduce it if you make a copy of your .mozilla directory, delete the .mozilla dir, and start firefox.

then the tab feature won't work as default. you have to go to the settings of firefox, switch the button to "open in new window" then  switch it back and now it works.

---

### Post by galileon on 2006-11-02
> **dskloet said:**
> and middle clicking on the tab closes it (which is highly annoying).

some would consider it a very useful feature! ;)

---

### Post by dskloet on 2006-11-02
Thanks loko, I'll try it when my laptop returns from repair.
> **galileon said:**
> some would consider it a very useful feature! ;)
Apparently, but I'd like to turn it off (even if I can't load the URL). Just like the Open-All-Bookmarks-In-This-Folder-With-One-Click feature, very annoying.

---

### Post by speedsix on 2006-11-02
I noticed this also.

---

