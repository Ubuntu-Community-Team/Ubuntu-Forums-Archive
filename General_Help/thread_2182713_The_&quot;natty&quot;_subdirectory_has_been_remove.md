---
title: "The &quot;natty&quot; subdirectory has been removed from ppa.launchpad.net/jonabeck/ppa/ ?"
date: 2013-10-22
forum: General Help
---

### Post by Bruce_Ying on 2013-10-22
Hello,

I'm sticking to Ubuntu 11.04 for the product which I've been developing, and perhaps won't upgrade to Ubuntu 12.04 or newer releases.
I used to install iFuse on my Natty platform by including below entry in my /etc/apt/sources.list
deb [http://ppa.launchpad.net/jonabeck/ppa/ubuntu](http://ppa.launchpad.net/jonabeck/ppa/ubuntu) natty main

However, as I ran "sudo apt-get update" today, I got 
"W: Failed to fetch [http://ppa.launchpad.net/jonabeck/ppa/ubuntu/dists/natty/main/binary-i386/Packages&#65292;404](http://ppa.launchpad.net/jonabeck/ppa/ubuntu/dists/natty/main/binary-i386/Packages&#65292;404)  Not Found"
error message, and as I looked for the PPAs for Natty at <http://ppa.launchpad.net/jonabeck/ppa/ubuntu/dists/>
there exist only four sub-directories for hardy, intrepid, jaunty and karmic.

Were the missing PPAs for the other legacy Ubuntu releases -- namely "natty" and the later ones -- accidentally removed 
or are they gone forever?

Thanks.

-- Bruce

---

### Post by Bruce_Ying on 2013-10-23
Rescued by Google -- just found that I'm able to download a package for iFuse v 1.1.1-2 at:
[https://launchpad.net/ubuntu/natty/i386/ifuse](https://launchpad.net/ubuntu/natty/i386/ifuse)

---

