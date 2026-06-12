---
title: "trying to get wget to act like flashgot"
date: 2013-02-26
forum: General Help
---

### Post by JohnnyC35 on 2013-02-26
I have used Flashgot on Firefox to get a list of torrents from different pages, i.e. eztv. I am trying to do this with wget, so that each day it would run and automatically download the days torrents, which would then be fed to my torrent client.
I haven't seen a way to call flashgot from the command line so I've been trying wget.
thus far, 
wget [http://eztv.it/sort/100/](http://eztv.it/sort/100/)                              only gets me the index file
wget -k [http://eztv.it/sort/100/](http://eztv.it/sort/100/)                         no change
wget --level=1 [http://eztv.it/sort/100/](http://eztv.it/sort/100/)            no change
wget -r [http://eztv.it/sort/100/](http://eztv.it/sort/100/) and wget -m [http://eztv.it/sort/100/](http://eztv.it/sort/100/)
   seem to download the entire website but not the torrent links. I cancelled that operation as I figure the admin would be very unhappy
wget -k -H [http://eztv.it/sort/100/](http://eztv.it/sort/100/)    still only the index file

finally I ran with --debug and I got a bunch of stuff but this stood out

Skipping [http://extratorrent.com/torrent_download/2990588/NewGamePlus+S02E08+HDTV+x264-NGPcRew+%5Beztv%5D.torrent](http://extratorrent.com/torrent_download/2990588/NewGamePlus+S02E08+HDTV+x264-NGPcRew+%5Beztv%5D.torrent) at position 173178.


not entirely sure what I need to do at this point. Ideally I would just look at what Flashgot does, and use that as it uses wget. but I am not able to read that fast as it zooms but, I can scroll up, and the people of the internets dont seem to have much on it either.  Thanks for any assistance :)

---

