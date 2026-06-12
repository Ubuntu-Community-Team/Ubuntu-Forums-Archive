---
title: "Ubuntu SERVER (console) HELP"
date: 2006-10-19
forum: General Help
---

### Post by commandercup on 2006-10-19
Well i've been following a linux tutorial at [http://www.cstrike-planet.com/tutorial/1/6](http://www.cstrike-planet.com/tutorial/1/6) for isntalling a cs 1.6 server on linux, and when i get to the part where you type, wget [http://www.cstrike-planet.com/dls/hldsupdatetool.bin](http://www.cstrike-planet.com/dls/hldsupdatetool.bin) and enter, it gives me this error, "Resolving http... failed: Temporary failure in name resolution." what does that mean? network error? what?

---

### Post by beerorkid on 2006-10-19
> **commandercup said:**
> Well i've been following a linux tutorial at [http://www.cstrike-planet.com/tutorial/1/6](http://www.cstrike-planet.com/tutorial/1/6) for isntalling a cs 1.6 server on linux, and when i get to the part where you type, wget [http://www.cstrike-planet.com/dls/hldsupdatetool.bin](http://www.cstrike-planet.com/dls/hldsupdatetool.bin) and enter, it gives me this error, "Resolving http... failed: Temporary failure in name resolution." what does that mean? network error? what?

hmmmm I just put in ```
wget http://www.cstrike-planet.com/dls/hldsupdatetool.bin
``` and it was fine for me.  Gotta be a DNS problem or something.

try ```
wget http://64.81.79.41/dls/hldsupdatetool.bin

```
which worked for me as well.

PS: just did a ping [www.cstrike-planet.com](www.cstrike-planet.com) to find the ip addy

---

