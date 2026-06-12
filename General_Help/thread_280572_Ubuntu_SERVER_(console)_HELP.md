---
title: "Ubuntu SERVER (console) HELP"
date: 2006-10-19
forum: General Help
---

### Post by commandercup on 2006-10-19
Well i've been following a linux tutorial at [http://www.cstrike-planet.com/tutorial/1/6](http://www.cstrike-planet.com/tutorial/1/6) for isntalling a cs 1.6 server on linux, and when i get to the part where you type, wget [http://www.cstrike-planet.com/dls/hldsupdatetool.bin](http://www.cstrike-planet.com/dls/hldsupdatetool.bin) and enter, it gives me this error, "Resolving http... failed: Temporary failure in name resolution." what does that mean? network error? what?

---

### Post by kidders on 2006-10-19
Hi there,

This means you're having trouble finding an IP address for [www.cstrike-planet.com](www.cstrike-planet.com). It's 64.81.79.41 (reverse DNS resolves to dslreports-west2.speakeasy.net), by the way.

To solve your immediate problem (ie the "wget" that won't work), try **wget [http://64.81.79.41/dls/hldsupdatetool.bin](http://64.81.79.41/dls/hldsupdatetool.bin)**. Of course, you'll need to address the underlying issue at some point ... check out your DNS settings ... they may be incorrect.

What's in your /etc/resolv.conf?
Are you running a DNS server?

---

