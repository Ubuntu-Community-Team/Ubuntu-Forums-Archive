---
title: "Upgrading from DapperDrake to Edgy"
date: 2007-10-12
forum: General Help
---

### Post by mmistroni on 2007-10-12
hi all, 
i am trying to move to Feisty (from Dapper drake)..
by reading docs on ubuntu site, path is to first upgrade to Edgy and then to Feisty

i followed steps suggested in guides here , but while upgrading i got following problem

failed to fetch [http://wine.lowvoice.nl/apt/dists/dapper/Release.gpg](http://wine.lowvoice.nl/apt/dists/dapper/Release.gpg) Could
not resolve 'wine.lowvoice.nl'
Failed to fetch
[http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz301](http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz301)
Moved Permanently
Failed to fetch
[http://wine.lowvoice.nl/apt/dists/dapper/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/dapper/main/binary-i386/Packages.gz) Could
not resolve 'wine.lowvoice.nl'

failed to fetch [http://wine.lowvoice.nl/apt/dists/dapper/Release.gpg](http://wine.lowvoice.nl/apt/dists/dapper/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz](http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz) 301 Moved Permanently
Failed to fetch [http://wine.lowvoice.nl/apt/dists/dapper/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/dapper/main/binary-i386/Packages.gz)  Could not resolve 'wine.lowvoice.nl'


i was wondering, has anyone found those problems? how can i fix them?

thanks and regards
 marco

---

### Post by cmnorton on 2007-10-12
I wound up having to comment out lines in /etc/apt/sources.list, until the upgrade would run through completely. It would not hurt to keep a copy of this file, so you'll know what was there after the upgrade. Your errors don't match the ones I had or read about, but it probably cannot hurt to try this method. 

Once you have upgraded, you can uncomment (or add back if not there) those lines and try a refresh.

---

