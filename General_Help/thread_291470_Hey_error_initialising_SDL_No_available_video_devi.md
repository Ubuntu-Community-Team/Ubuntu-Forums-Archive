---
title: "Hey error initialising SDL: No available video device"
date: 2006-11-02
forum: General Help
---

### Post by Lukasz Tarkowski on 2006-11-02
Hey how are ya
I get this error 

error initialising SDL: No available video device

when trying to run blockrage.
I have configured and make make install it created evrything it just won't start cause of that error :(
My graphic card is ati radeon

---

### Post by trunks14 on 2007-12-08
Ohh lord this just happened to me. You won't believe my noobness but my problem was that I forgot to run:

> make install

after

> ./configure
> make

That was causing the environmental variable SDL_VIDEODRIVER not to work.

it sounds stupid but try it XD

old post but might help someone googling it.

---

