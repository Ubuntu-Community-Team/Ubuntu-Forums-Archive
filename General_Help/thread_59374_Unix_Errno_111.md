---
title: "Unix Errno 111"
date: 2005-08-23
forum: General Help
---

### Post by diNunes on 2005-08-23
Hi, I'm using the TG2 application to generate traffic over a network using UDP. The problem is that at certain point diferent for every test the client generates this error: 

36.105328	Transmit 	192.168.246.58.4320	12941	0	Unix Errno 111

The decoder stops decoding the file because of this error, but the client keeps sending packtes even after the error!

Those anyone have a clue about what's causing this error?

Thanks!!

---

### Post by arnieboy on 2005-08-23
[QUOTE=diNunes]Hi, I'm using the TG2 application to generate traffic over a network using UDP. The problem is that at certain point diferent for every test the client generates this error: 

36.105328	Transmit 	192.168.246.58.4320	12941	0	Unix Errno 111

The decoder stops decoding the file because of this error, but the client keeps sending packtes even after the error!

Those anyone have a clue about what's causing this error?

Thanks!![/QUOTE]
111 corresponds to connection refused error.
It sounds like it is something local to your machine.
Have you tried running tg to a different port number?  Is there something else using
that port? Have you run out of resources?

---

### Post by diNunes on 2005-08-24
I already tried diferent ports and I got the same error!
I don't have anything using this ports besides this application!  :-? 

Could be something else?

---

### Post by arnieboy on 2005-08-24
[QUOTE=diNunes]I already tried diferent ports and I got the same error!
I don't have anything using this ports besides this application!  :-? 

Could be something else?[/QUOTE]
yes it could be your computer running out of resources like memory.

---

### Post by diNunes on 2005-08-24
I forgot to mention that... 

I repeat the test and I check the resources and I have plenty of resources!

Any sugestions?

---

