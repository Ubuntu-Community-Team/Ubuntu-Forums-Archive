---
title: "few Num pad numbers not working"
date: 2017-11-28
forum: General Help
---

### Post by dante5047 on 2017-11-28
I have Ubuntu 16.04 LTS installed on my laptop Acer Aspire (Dual boot alongside Windows 7). In the numpad, the numbers 1,3,5,7,9 are working properly. but I'm unable to type 2,4,5,6. I've tried turning NumLock on and off. Even the navigation isn't working using those keys. Anyone else encountered this problem?

---

### Post by HermanAB on 2017-11-28
Run xev and see what it returns.

If xev works, then you can remap the keys with xmodmap.  If xev doesn't work, then you probably need a new keyboard.

---

