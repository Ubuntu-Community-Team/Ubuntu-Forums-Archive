---
title: "And.....You're Right on Time!"
date: 2008-04-23
forum: General Help
---

### Post by Exsecrabilus on 2008-04-23
Do they release each new distribution just at midnight or around that time?

Because if they are, I'm willing to stay up late just for that.

---

### Post by imbjr on 2008-04-23
Close to UK midnight, I shall be running the following:

> 
#!/bin/sh

DOWNLOADED="N"
while [ $DOWNLOADED = "N" ]
do
	if 
		wget [http://releases.ubuntu.com/hardy/ubuntu-8.04-desktop-i386.iso.torrent](http://releases.ubuntu.com/hardy/ubuntu-8.04-desktop-i386.iso.torrent)
	then
		DOWNLOADED="Y"
	else
		DOWNLOADED="N"
		sleep 300
	fi
done

deluge ubuntu-8.04-desktop-i386.iso.torrent


Every 5 minutes it will look for what I expect the appropriate BitTorrent will be called. Once it gets it, deluge will download the ISO.

Feel free to adopt, but as ever - buyer beware.

---

### Post by imbjr on 2008-04-23
*Sigh*

Why is it that something I quote gets mangled!?

Hovering one's cursor over the torrent URL will however reveal the correct location.

---

### Post by Exsecrabilus on 2008-04-23
How faster or slower is UK compared to the New York-Pennsylvania-Connecticut-New Jersey-Maryland area?

---

### Post by imbjr on 2008-04-23
Canonical is UK-owned, so the earliest time to expect to see 8.4 release is 12 midmight BST.

As for your location, NY time is 5 hours behind BST, around 7 pm NY local time is when to start expecting the ISO/torrent to appear.

---

### Post by twright on 2008-04-23
just copy and paste and the outcome will be normal> **imbjr said:**
> *Sigh*

Why is it that something I quote gets mangled!?

Hovering one's cursor over the torrent URL will however reveal the correct location.

why not just upgrade to the release candidate using update-manager -d, this time updating via update manager seems to be smoother but it still seems to break suspend and hibernate for me

---

