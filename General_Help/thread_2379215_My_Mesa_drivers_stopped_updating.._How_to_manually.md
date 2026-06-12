---
title: "My Mesa drivers stopped updating.. How to manually install the latest ones?"
date: 2017-12-02
forum: General Help
---

### Post by johnstefnds on 2017-12-02
For some reason my drivers remain at Mesa 17.3.0-rc4 and LLVM 5.0.0
  Now the latest mesa is 17.4 and LLVM 6
  But for some reason I dont get any updates... if i try sudo apt  upgrade nothing.. if I try the graphical updater it tells me that my  software is up to date..
  I added padoka and nothing I added oibaf nothing... now I purged  padoka (as instructed in the main page of that guy who maintains it) but  again nothing...
  What should I do? I use ubuntu 17.10 and my kernel is 4.15.0-041500rc1-lowlatency

---

### Post by mc4man on 2017-12-02
You would get what you want from the  padoka unstable ppa.
[https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/mesa](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/mesa)

So remove oibaf, remove the padoka stable ppa (if enabled), add the unstable, update sources, then check
(- run this if need be to see versions, the one you mentioned in post was likely from the padoka stable ppa
apt policy libegl1-mesa

---

