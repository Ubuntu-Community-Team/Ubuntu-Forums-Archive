---
title: "Mythtv and backend server cannot communicate"
date: 2006-12-07
forum: General Help
---

### Post by fatalfurry on 2006-12-07
I had mythtv working for the first time this afternoon I am using this guide.
[http://www.mythtv.org/wiki/index.php/Ubuntu_Edgy_Installation_From_Source](http://www.mythtv.org/wiki/index.php/Ubuntu_Edgy_Installation_From_Source)
after doing a apt-get update and upgrade it now gives me this error

2006-12-07 00:38:00.681 MainServer::HandleVersion - Client speaks protocol version 31 but we speak 30!

I have looked in mythtv to find where I can change this but idk what Im doing yet. Does anyone know what to do?

---

### Post by superm1 on 2006-12-07
If you built from source prior to installing binaries, remove any /usr/local/lib/*myth*
/usr/local/bin/*myth*
/usr/local/share/mythtv/*
/usr/local/include/mythtv/*

The version in the edgy repositories speaks protocol 31 which was included in 0.20-fixes.

---

