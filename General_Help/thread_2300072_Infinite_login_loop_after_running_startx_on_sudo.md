---
title: "Infinite login loop after running startx on sudo"
date: 2015-10-23
forum: General Help
---

### Post by anthony78 on 2015-10-23
After stupidly launching startx on sudo, my Ubuntu screen went black and took me to the login screen. I'm unable to login except as a guest and this is really frustrating. I've spent the better part of a day scouring countless forums and there are other people that have had the same experience. The only difference is that they are able to login to a console via CTRL+ALT+F1 to F6 and check/change/delete the ownership of  Xauthority file. Whenever i do this, the console asks me to log in and subsequently rejects my login as incorrent -_-.
Can anybody out there help me out?
I'm running ubuntu 13.10.

---

### Post by tturrisi on 2015-10-23
If you know your root pw you can login as root in recovery mode boot and do whatever you want to do.  And for future reference, sudo is never needed for startx.

---

### Post by anthony78 on 2015-10-23
What should i do once i'm logged in as root in recovery mode boot?

---

