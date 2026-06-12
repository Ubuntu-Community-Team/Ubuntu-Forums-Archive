---
title: "Update Problems"
date: 2013-01-28
forum: General Help
---

### Post by bigb0ss on 2013-01-28
12.04.1 LTS

Every 2 days or so, when I go to update my ubuntu, I get a Orange Triangle with a "!" 

 something like this...[http://drfishspawestville.co.za/Images/errorTriangle.GIF](http://drfishspawestville.co.za/Images/errorTriangle.GIF)

W:Failed to fetch [http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

*Note*  I have no cd drive with this netbook. It was a chromebook and put Ubuntu on it.


fix?



Thanks

---

### Post by bigb0ss on 2013-01-28
Sometimes there is an update for this and the triangle goes away and then, in 2 days it comes up again, I go to update and there is no update. 

I then proceed to restart the unit, it disappears and then reappears in few hours.

MAGIC.....please help me ;(


Thanks

---

### Post by claracc on 2013-01-28
I think the problem is that these ppas are not in the server, when I click on the first ppa address I obtain:

The requested URL /iaz/battery-status/ubuntu/dists/precise/main/source/Sources was not found on this server

So, better, you uncheck these ppas from software sources or remove them. The updating behaviour is the normal one in this case.

---

### Post by arpanaut on 2013-01-28
Yes, nothing in this PPA since natty.
[http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/](http://ppa.launchpad.net/iaz/battery-status/ubuntu/dists/)

---

