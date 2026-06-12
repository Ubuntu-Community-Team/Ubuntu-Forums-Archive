---
title: "Corrupted graphics in RDP"
date: 2006-12-07
forum: General Help
---

### Post by leftcase on 2006-12-07
Hi there,

When using gnome-rdp or terminal server client in Ubuntu I'm getting some graphics corruption.

I'm using RDP to connect to a Win 2003 Server and I'm getting graphics corruption whenever I move or drag a window around the screen within the RDP session.

Any ideas folks?

---

### Post by Hurons on 2006-12-09
I am having the same issue. If there is a way to solve this I would run all my clients as Edgy...



Anyone have suggestions?

Thank You,

Hurons

---

### Post by leftcase on 2006-12-12
Strange thing is, i've also got an Edgy box set up at work. RDP runs fine on that one, although it's using different hardware...

Graphics or driver problem perhaps?

Anyone...

---

### Post by technodigifreak on 2006-12-12
I've always had a problem with text displaying oddly though an RDP session to a windows server.  It doesn't bother me any, but I know it would bother some users.  Any fix would be greatly appreciated.

---

### Post by ayoli on 2006-12-12
i use rdesktop package from [http://getdeb.net](http://getdeb.net) and have no graphics pb, just can have more than 16bits colors.

edit: its a command line tool, you can use like this to begin:
```
rdesktop -u Administrateur -k fr -f host.adress.com -p -
```
-k fr is for key board layout, replace with yours
-f for full screen (ctrl alt enter to toggle)
-p - for password prompt

---

### Post by Hurons on 2006-12-17
any one else have these graphics issues? The screen bleeds together when scrolling applications. If anyone has a fix, or knows the best settings, please let us know.


Thank You

---

### Post by ayoli on 2006-12-18
> **Hurons said:**
> any one else have these graphics issues? The screen bleeds together when scrolling applications. If anyone has a fix, or knows the best settings, please let us know.


Thank You

did you try rdesktop instead of tsclient ? i experimented same problems as you with tsclient so i tried rdesktop (see my  post above) and it works great no more scroll problem a 16bit colors instead of 256 (tsclent was almost transparent with more than 256 colors).

---

### Post by dad311 on 2007-01-05
I had the same issue until I upgraded rdesktop to version 1.5.

---

### Post by Hurons on 2007-01-21
> **dad311 said:**
> I had the same issue until I upgraded rdesktop to version 1.5.

It worked....thanks a bunch

---

### Post by phocker on 2007-03-02
Upgrading to the 1.5 rdesktop has also fixed the problem on my desktop too. Huzzah!

- Paul

---

