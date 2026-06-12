---
title: "Transmission build .90"
date: 2007-10-24
forum: General Help
---

### Post by misfitpierce on 2007-10-24
Is it possible for someone to build this 64 bit or w/e. I tried for an hour or so and its a no go. Im not very good at building packages and would appreciate it to the upmost if someone could build and stick in here or on getdeb in 32bit and 64bit or either. Thankyou a ton if possible. I prefer 64 bit though :)

---

### Post by misfitpierce on 2007-10-24
Noone can assist in helping me build this package? I want transmission with encryption badly. I like Transmission the best so anyone capable of building and making packages please help :)

---

### Post by rabsteen on 2007-10-24
i'm having trouble compiling from source as well.  will work on it.

---

### Post by jpmontalbo on 2007-10-25
> **rabsteen said:**
> i'm having trouble compiling from source as well.  will work on it.

I was having trouble compiling the source as well until I installed these two packages.

libevent-dev and libssl-dev

Let me know if it works for you.

---

### Post by FredB on 2007-10-25
Deluge is also using encryption and transmission seems to be hated on some torrents site.

Did you try deluge 0.5.6 ?!

->[]

---

### Post by Morbett on 2007-10-25
I also can't seem to build this.  Anyone have a .deb?

---

### Post by misfitpierce on 2007-10-25
Good news... Transmission deb on getdeb.net... Woooo. I tried deluge but like transmission interface best. Also its way lighter... :)

---

### Post by FredB on 2007-10-25
> **misfitpierce said:**
> Good news... Transmission deb on getdeb.net... Woooo. I tried deluge but like transmission interface best. Also its way lighter... :)

Indeed... 5 times lighter, but is there some plugins like blocking list ? :)

Anyway, prefer deluge to transmission ;)

---

### Post by Morbett on 2007-10-26
I installed the .deb from GetDeb.net, but my version still says 0.82 in the Help -> "About Transmission".  This is the version that loads using the command:  transmission-gtk

Also, there are now two Transmission entries in my Internet Menu :  "Transmission" and "Transmission BitTorrent Client".  Hmm..

---

### Post by craigyjack on 2007-10-29
i just compiled transmission .90 from source yesterday, and it went fine. at first i got error because i didnt have libssl-dev package installed, but i installed that package, did ./configure again, and then makea d make install went fine and i am running transmission now.

what problems are you guys having compiling it exactly?

---

