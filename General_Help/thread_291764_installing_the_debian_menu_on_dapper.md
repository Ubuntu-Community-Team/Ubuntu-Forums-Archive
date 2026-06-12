---
title: "installing the debian menu on dapper"
date: 2006-11-02
forum: General Help
---

### Post by djroadrash on 2006-11-02
hi everyone, after selling my ubuntu box that had brezzy in it, i have been playing with kanotix and os x, but when i tried to install kanotix in my thinkpad a21m and getting a really weird error ( BUG: soft lockup detected on CPU#0! ), i decided to come back to ubuntu on its dapper version, so i installed it and as i started to configure it to my liking, i got stock trying to get the debian menu to install, i tried the old method with
```
sudo apt-get install menu
update-menus
```
but nothing happened, so after digging a little on the net i found the solution, so if u have this problem this are the next steps to follow, after u put the above commands, do the next:
```
sudo dpkg-reconfigure menu
sudo dpkg-reconfigure menu-xdg

```
after that restart your computer and the menu will be there. not too complicated.
peace
armando:)

---

### Post by djroadrash on 2006-11-02
:)

---

