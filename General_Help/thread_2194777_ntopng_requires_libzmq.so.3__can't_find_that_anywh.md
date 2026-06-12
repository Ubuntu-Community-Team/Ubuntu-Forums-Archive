---
title: "ntopng requires libzmq.so.3 ?? can't find that anywhere"
date: 2013-12-20
forum: General Help
---

### Post by dhsmith on 2013-12-20
ntopng: error while loading shared libraries: libzmq.so.3: cannot open shared object file: No such file or directory


This error after a clean install of the package, no other requirements stated. Can't find anything but libzmq.so.1 No reference to this problem on NTOP site or anywhere else - I'm stuck

---

### Post by Toz on 2013-12-20
Hello and welcome to the forums.

Which version of Xubuntu are you using? libzmq.so.3 is part of the libzmq3 package, but its only available for saucy (13.10) and later - earlier Xubuntu versions don't have this package included. See: [http://packages.ubuntu.com/search?keywords=libzmq3]("http://packages.ubuntu.com/search?keywords=libzmq3"). If you have an earlier version, you're probably looking at having to compile it yourself (googling doesn't find a PPA that you can use). Website: [http://zeromq.org/]("http://zeromq.org/").

---

### Post by dhsmith on 2013-12-20
Oh rats! Got me. That old monitor box is still on raring...  I see it available on my saucy boxen. THANKS - good catch. Odd that google turns up so little. Thanks for the welcome - hope I can contribute. Gonna have to call this one SOLVED (if I can figure out how)  :P

---

### Post by Toz on 2013-12-20
> **dhsmith said:**
> Gonna have to call this one SOLVED (if I can figure out how)  :P
Its under the "Thread Tools" link towards the top of the page.

Enjoy your stay.

---

