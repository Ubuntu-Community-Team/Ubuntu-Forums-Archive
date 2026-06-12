---
title: "WINE and JACK not working..."
date: 2005-10-24
forum: General Help
---

### Post by GameGod on 2005-10-24
Hey everyone,

I'm trying to get WINE working with jack, and it's just not happening.
I've edited my wine config to use the jack driver instead of the OSS driver (the default, I believe), and I launch my jack server with "jackd -d alsa", which works fine (this has been tested with other jack apps...)

When I fire up a WINE application (Buzz, in this case), I get a "cannot open wave-out blah blah"... Anyone got any ideas why this isn't working?

Here's your other hint: When I try to make WINE use it's ALSA driver instead of the OSS (or jack) one, it also doesn't work (same error as if I was trying to use jack...)

Thanks!

GameGod

---

