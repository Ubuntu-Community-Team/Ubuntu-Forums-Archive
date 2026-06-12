---
title: "Sound-juicer gives up with musicbrainz too early ?"
date: 2005-10-03
forum: General Help
---

### Post by alci on 2005-10-03
Hi,

I can't get sound-juicer to find artist / album / tracks names out of Musicbrainz.
It always reports Unknown Artist / Album / Track.

When I launch it from shell, I get this message when reading the cd :

This CD could not be queried: Cannot find server: mm.musicbrainz.org

If I do a ping mm.musicbrainz.org , I get :

PING musicbrainz.org (216.218.240.152) 56(84) bytes of data.
64 bytes from rdns.152.240.218.216.fre.communitycolo.net (216.218.240.152): icmp_seq=1 ttl=48 time=670 ms
64 bytes from rdns.152.240.218.216.fre.communitycolo.net (216.218.240.152): icmp_seq=2 ttl=48 time=670 ms
64 bytes from rdns.152.240.218.216.fre.communitycolo.net (216.218.240.152): icmp_seq=3 ttl=48 time=671 ms
64 bytes from rdns.152.240.218.216.fre.communitycolo.net (216.218.240.152): icmp_seq=4 ttl=48 time=559 ms

--- musicbrainz.org ping statistics ---
5 packets transmitted, 4 received, 20% packet loss, time 4359ms
rtt min/avg/max/mdev = 559.033/642.804/671.038/48.376 ms

Obviously not the ideal networking conditions, but isn't sound-juicer too picky on this ?

It really makes it less than optimal.

Any comments ?

Franck

---

