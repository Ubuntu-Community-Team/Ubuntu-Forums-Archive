---
title: "Streaming TV card/FM tuner via network"
date: 2005-06-07
forum: General Help
---

### Post by tbasten on 2005-06-07
Hi.

I was wondering if it is possible to Stream my TV card/FM tuner via the network. My card is working fine. Now exactly what i would like to do is have it so my flat mates can watch tv on there computer via my computer, mean using my TV card via network so that they can watch different channels. The same with my fm tuner. Now is there some software that can support this for the server side (ubunut) and a client side (windows). If not is it possible to make one (myself)

Cheers

Tim

---

### Post by sgtstadanko on 2005-06-07
[QUOTE=tbasten]Hi.

I was wondering if it is possible to Stream my TV card/FM tuner via the network. My card is working fine. Now exactly what i would like to do is have it so my flat mates can watch tv on there computer via my computer, mean using my TV card via network so that they can watch different channels. The same with my fm tuner. Now is there some software that can support this for the server side (ubunut) and a client side (windows). If not is it possible to make one (myself)

Cheers

Tim[/QUOTE] it would not be possible for them to watch different channels on the same card at the same time.  Now if you had multiple tv cards, then you could do that.  You might want to check out VideoLan for some basic streaming to their computers.  Its quite featureful.  I have streamed content with VLC and it works well.  If you are interested in doing linux TV card stuff, I highly suggest you take a look at MythTV ([www.mythtv.org)](www.mythtv.org)).  It does tv recording, time shifting , plays movie files, plus music, games, dvd, and about a zillion other things. I think its one of the best open source apps around.

---

### Post by tbasten on 2005-06-07
Thanks for that. Thats help answered a few questions, Just after radio now.

---

### Post by sgtstadanko on 2005-06-07
[QUOTE=tbasten]Thanks for that. Thats help answered a few questions, Just after radio now.[/QUOTE]

My tv card doesn't have radio, but I believe there is some support in mythtv for the FM Tuner.  Head on over to the mailing list archive and do a search....[http://www.gossamer-threads.com/lists/mythtv/users/](http://www.gossamer-threads.com/lists/mythtv/users/)

---

### Post by tbasten on 2005-06-09
[QUOTE=sgtstadanko]My tv card doesn't have radio, but I believe there is some support in mythtv for the FM Tuner.  Head on over to the mailing list archive and do a search....[http://www.gossamer-threads.com/lists/mythtv/users/](http://www.gossamer-threads.com/lists/mythtv/users/)[/QUOTE]


Hey, Thanks, I see to be having problems with mythtv. When i try and start anything i says the follow

```
tbasten@Dyna:~ $ mythtv
mythtv: error while loading shared libraries: libmp3lame.so.0: cannot open shared object file: No such file or directory
```

libmp3lame doesnt seem to be in my apt-get respositories by doing an apt-cache search libmp3lame

```
tbasten@Dyna:~ $ apt-cache search libmp3lame
tbasten@Dyna:~ $
```

---

