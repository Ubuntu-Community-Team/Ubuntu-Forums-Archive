---
title: "Juk not getting track info from internet"
date: 2005-04-10
forum: General Help
---

### Post by darkaudit on 2005-04-10
For the last few days, when I try to guess tag info from the internet, I get 'Error connecting to musicbrainz server.' I looked at .xsession-errors, but I didn't see anything useful.

There's always the possibility that the musicbrainz server doesn't like my ip address, since my ISP is Verizon, and they aren't exactly on everybody's good side lately. I just can't prove this at the moment.

Anyone else having connection troubles with musicbrainz and Juk?

---

### Post by darkaudit on 2005-04-10
Sorry for the bump, but I'm also getting the same error with Amarok as well. The error happens instantly. It's as if the app isn't even trying to connect to the server. I tried installing the -dev package, but no luck.

---

### Post by riffic on 2005-04-11
[QUOTE=darkaudit]Sorry for the bump, but I'm also getting the same error with Amarok as well. The error happens instantly. It's as if the app isn't even trying to connect to the server. I tried installing the -dev package, but no luck.[/QUOTE]
I'm getting this with amarok as well. Guess its a real bug and not a fluke, since it started doing this quite recently, and previously worked normally as expected.

---

### Post by darkaudit on 2005-04-11
I filed a bug against libmusicbrainz4, and also found an upstream bug report that suggests the package was inadequately compiled. As a result, the net functions don't exist.

---

### Post by darkaudit on 2005-04-11
This is important, so forgive the bump.

The problem isn't libmusicbrainz at all. It's libtunepimp-bin. The package description clearly states that mp3 is supported. But when trm is run, it says that mp3 is *not* supported. I did an apt-build --reinstall install libtunepimp-bin on the assumption that this new build would restore mp3 support.

I was correct. After installing the rebuilt packages, I can once again query the musicbrainz servers for tag info on my mp3's.

The release package of libtunepimp-bin was incorrectly compiled. MP3 support is missing.

---

### Post by riffic on 2005-04-13
[QUOTE=darkaudit]This is important, so forgive the bump.

The problem isn't libmusicbrainz at all. It's libtunepimp-bin. The package description clearly states that mp3 is supported. But when trm is run, it says that mp3 is *not* supported. I did an apt-build --reinstall install libtunepimp-bin on the assumption that this new build would restore mp3 support.

I was correct. After installing the rebuilt packages, I can once again query the musicbrainz servers for tag info on my mp3's.

The release package of libtunepimp-bin was incorrectly compiled. MP3 support is missing.[/QUOTE]
can you package that .deb and host it somewhere? 

I really want to thank you for looking into this and finding a solution

---

### Post by darkaudit on 2005-04-13
The apt-build also rebuilt all the other libtunepimp packages, such as the python ones. Apt-build will go and get what it needs to build, and the rebuild really didn't take that long. Once it's done, just go into synaptic and the packages will all be there waiting for you to install (I had an odd error about force-yes that I didn't understand, so i had to install the final .debs from Synaptic).

---

### Post by riffic on 2005-04-13
[QUOTE=darkaudit]The apt-build also rebuilt all the other libtunepimp packages, such as the python ones. Apt-build will go and get what it needs to build, and the rebuild really didn't take that long. Once it's done, just go into synaptic and the packages will all be there waiting for you to install (I had an odd error about force-yes that I didn't understand, so i had to install the final .debs from Synaptic).[/QUOTE]
apt-build is giving me some weird errors, can you upload the debs?

thanks

---

