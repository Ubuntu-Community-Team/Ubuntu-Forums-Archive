---
title: "Q3VGroupBox"
date: 2007-12-23
forum: General Help
---

### Post by ottothecow on 2007-12-23
I'm trying to compile a piece of software on dapper-server LTS and it is complaining about missing Q3VGroupBox.

My non-server gutsy box compiles just fine, if I look in /usr/include/qt4/Qt3Support/ it has both Q3VGroupBox and Q3GroupBox.  my dapper only has Q3GroupBox and not the Q3V.

I would think that this would be a part of libqt4-devel but apparently it is not.  Anyone know how I can get that file?

---

### Post by ottothecow on 2007-12-23
So, as soon as I posted this, I realized that this is an issue with the qt4 version in dapper LTS

I need QT4.2 for that particular function.  That package exists in backports but I question the idea of sticking with an LTS release and then pulling from backports.

Would I be better off just using gutsy-server and hoping that everything moves easily to the upcoming LTS release?

---

### Post by ottothecow on 2007-12-23
or else I am just stupid and qt4.2 isn't even in dapper-backports

I'll just try gutsy and hope its an easy move to the next LTS

---

