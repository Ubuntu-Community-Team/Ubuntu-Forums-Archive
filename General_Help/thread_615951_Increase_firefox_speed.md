---
title: "Increase firefox speed"
date: 2007-11-17
forum: General Help
---

### Post by rye_ on 2007-11-17
Firefox has been getting a lot of flack about speed lately.  I find the following procedure (not authored by me) works very well in improving speed.

1) Open Firefox
2) Type "about:config" into the address bar and hit return. Scroll down and look for the following entries:
network.http.pipelining network.http.proxy.pipelining network.http.pipelining.maxrequests
3) Alter the entries as follows:
Set "network.http.pipelining" to "true" (simply double click the entry)
Set "network.http.proxy.pipelining" to "true" (simply double click the entry)
Set "network.http.pipelining.maxrequests" to some number like 30. This means it will make 30 requests at once.
Now right-click anywhere and select New-> Integer. Name it "nglayout.initialpaint.delay" and set its value to "0". This
value is the amount of time the browser waits before it acts on information it recieves.
4) Close Firefox
5) Re-open and test for speed

---

### Post by seanyseansean on 2007-11-17
That's not the best way to fix the problem. All you're doing is hammering the server you're connecting to. A properly configured one will throw away the extra requests, leading to timeouts, and others won't appreciate the load you're putting on them.

If speed is your primary concern, use Opera instead - it's in the repositories.

---

### Post by x64Jimbo on 2007-11-17
A.K.A. [Fasterfox]("https://addons.mozilla.org/en-US/firefox/addon/1269")

---

### Post by TheExplorer on 2007-11-17
An outdated fix to encrease speed that was actual long ago...
Now FF is fast for me enough. Well, the first or cold start is a bit long but it depends on the number of extensions installed. Hot start is extremely fast (faster than Opera under Ubuntu). That's the facts. I've just realized how to tweak unused/unimportant modules down. The system eats only 150 megs of memory with all the functionality still present (Gutsy 7.10). Envy me :)

---

### Post by misfitpierce on 2007-11-17
8 on pipelining is quite sufficient

---

