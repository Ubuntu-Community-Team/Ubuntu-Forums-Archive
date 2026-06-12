---
title: "Setting super key as a ctrl key in Xubuntu"
date: 2013-07-08
forum: General Help
---

### Post by ccoulter on 2013-07-08
Hello,

I am running Xubuntu on the Samsung ARM chromebook; I used the ChrUbuntu install script--works great. It is a chromebook, so there is a search key located where caps lock typically is located. The search key is currently configured to work as a super key.

I am starting to learn emacs and I would really like to remap the search/super key as a control key. Also, ideally, I would like the right ctrl key to then serve as a super key.

I have scoured the internet for advice on how to do this, but I haven't been able to find anything which addresses my case in particular (a chromebook running Xubuntu), so any help will be greatly appreciated.

Thanks!

---

### Post by HermanAB on 2013-07-09
The program xev will tell you the key number and xbindkeys can then be used to configure the keymap.  Read the man pages and Google for howtos on xbindkeys.

---

