---
title: "--keyserver is not understood"
date: 2014-08-16
forum: General Help
---

### Post by parkergking on 2014-08-16
Hey guys, I've been using Ubunutu a few days now. Decided I wanted to try and get the Debian preview version of Spotify, I was using the Windows version with Wine and having crashing, some people said the preview version is actually more stable.

So, I started following the instructions here: [https://www.spotify.com/us/download/previews/](https://www.spotify.com/us/download/previews/)

-I used sudo nano to edit the sources.list.

-Then, I got to the apt-get adv --keyserver terminal command and I get the error in the title, "--keyserver is not understood".

I tried to perform an apt-get update but it only returns this: "W: GPG error: [http://repository.spotify.com](http://repository.spotify.com) stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59"


I searched and searched for hours for an answer somewhere but none exist, I saw several people with the same issue who never received an answer. So, any help would be greatly appreciated, thanks.  ;)

---

### Post by steeldriver on 2014-08-16
Hello and welcome to the forums

Are you sure you typed the command correctly?

```

apt-**key** adv --keyserver ...

```

(not apt-**get** - that's a different command)

---

### Post by parkergking on 2014-08-16
> **steeldriver said:**
> Hello and welcome to the forums

Are you sure you typed the command correctly?

```

apt-**key** adv --keyserver ...

```

(not apt-**get** - that's a different command)

Wow.. I love you man.

But I hate myself for how simple my error was... Lmao..

Thanks a ton, and for the super fast response. :D

---

