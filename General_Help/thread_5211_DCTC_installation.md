---
title: "DCTC installation"
date: 2004-11-16
forum: General Help
---

### Post by cws on 2004-11-16
I'm desperately trying to compile DCTC version 0.85.9 so I could start compiling dc-qt. After running the configure script [SIZE=2]./autogen.sh[/SIZE] I've got different kinds of errors, which I was able to solve, but the latest one I can't figure out.

configure: error: BerkeleyDB include required.

??

I just don't know what to do and what hell does that mean... :)

---

### Post by dataw0lf on 2004-11-16
I think the package you need is called db4, I'm not sure (I'm at work right now).  Just do a search in synaptic for berkeley, look around, it should be in there somewhere.
Cheers, 
dataw0lf

---

### Post by cws on 2004-11-17
Strange. I installed all the db-4.2 packets available but still errors.

checking Berkeley Database library version... 4.2
checking for db_env_create in -ldb-4.2... no
checking for db_env_create in -ldb4... no
configure: error: db.h reports Berkeley DB version is 4.2 but no db-4.2 library exists

---

### Post by piedamaro on 2004-11-17
[QUOTE=cws]Strange. I installed all the db-4.2 packets available but still errors.

checking Berkeley Database library version... 4.2
checking for db_env_create in -ldb-4.2... no
checking for db_env_create in -ldb4... no
configure: error: db.h reports Berkeley DB version is 4.2 but no db-4.2 library exists[/QUOTE]
 It seems you installed the headers of a version, while you have another db version installed.

Since I use it, I reccomend to use the cvs version which contains important fixes. Unfortunately the development is dead, so you'll never find the next version with those fixes merged in.
Same deal for dc_gui2 (the gtk2 frontend).

I remember I've had issues compiling it too, it depends a lot on a specific db version. If you look at dctc forum, you'll find some helps on compiling dctc with berkley db.

Btw, it's not what I call a friendly interface, but it rocks!

---

### Post by cws on 2004-11-19
Ok. Thank you both. Didn't solve it yet, but I'm gonna! :)

---

### Post by flajus on 2006-11-03
Please can somebody help me i installed dctc and everything looks ok but when i connect to hub i down know how to search.
When i connect to hub i get this text and alots of more:


UINFO] ""alvis1 68612614339 Cable [(07)away,server] 'alvis@balticum-tv.lt' <LT>mp3<PWDC++ V:0.41,M:P,H:17/0/0,S:17>|
UINFO] ""orintuk 40459116146 LAN(T1) [(0B)away,fast] '' <LT>{10/15} [/] PeerWeb DC++<PWDC++ V:0.41,M:P,H:4/0/0,S:15>|
USER-] ""betmanas|
UINFO] ""orintuk 40459116146 LAN(T1) [(0B)away,fast] '' <LT>{10/15} [/] PeerWeb DC++<PWDC++ V:0.41,M:P,H:4/0/0,S:15>|
USER-] ""ciuwas|
USER-] ""seimaa|
UINFO] ""Vaflen 17084099771 LAN(T1) [(0B)away,fast] '' <LT>{8/9} [/] PeerWeb DC++<PWDC++ V:0.301,M:A,H:8/0/0,S:9>|
UINFO] ""Vaflen 17084099771 LAN(T1) [(0B)away,fast] '' <LT>{8/9} [/] PeerWeb DC++<PWDC++ V:0.301,M:A,H:8/0/0,S:9>|
UINFO] ""Vitioks 54873866921 LAN(T3) [(0B)away,fast] '' <LT>{2/25} [10M/10M] <PWDC++ V:0.41,M:P,H:12/0/0,S:25>|
UINFO] ""Vitioks 54873866921 LAN(T3) [(0B)away,fast] '' <LT>{2/25} [10M/10M] <PWDC++ V:0.41,M:P,H:12/0/0,S:25>|
UINFO] ""sn@iper-LT 29136943190 Cable [(01)] 'ciukci@one.lt' <LT>[10][/]:)<ApexDC++ V:0.2.2,M:A,H:2/0/0,S:20>|
UINFO] ""sn@iper-LT 29136943190 Cable [(01)] 'ciukci@one.lt' <LT>[10][/]:)<ApexDC++ V:0.2.2,M:A,H:2/0/0,S:20>|
UINFO] ""fATALeRRoR696 64643132756 2 [(09)fast] '' <LT><StrgDC++ V:2.02,M:P,H:13/0/0,S:13>|
UINFO] ""wiLeX_ 19374894635 LAN(T3) [(0B)away,fast] '' <MegaNET>{5/5} [/] PeerWeb DC++<PWDC++ V:0.4,M:P,H:3/0/0,S:9>|
UINFO] ""wiLeX_ 19374894635 LAN(T3) [(0B)away,fast] '' <MegaNET>{5/5} [/] PeerWeb DC++<PWDC++ V:0.4,M:P,H:3/0/0,S:9>|
UINFO] ""brisius 47771951373 0.005 [(01)] 'V-Y-T-A-U-T-A-S@one.lt' <MegaNET>coooooooooooooooooooooooooooooooool<++ V:0.698,M:A,H:29/0/0,S:25,O:29>|
UINFO] ""Bujokis 12691405649 1 [(01)] 'Bujokis@hotmail.com' <LT>[5]private<ApexDC++ V:0.2.2,M:P,H:9/1/0,S:10>|
UINFO] ""Bujokis 12691405649 1 [(01)] 'Bujokis@hotmail.com' <LT>[5]private<ApexDC++ V:0.2.2,M:P,H:9/1/0,S:10>|


i dont understand what to do . when i triyn to type /search like in windows dc++ it doesnt work , please can somebody explain to me? with examples if somebody can... i really would be gratefull if somebody help me:)

---

