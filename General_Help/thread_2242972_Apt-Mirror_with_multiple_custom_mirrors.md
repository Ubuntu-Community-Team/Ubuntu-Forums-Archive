---
title: "Apt-Mirror with multiple custom mirrors"
date: 2014-09-05
forum: General Help
---

### Post by jasoncal on 2014-09-05
Hi,
 I am looking for a solution to a particular issue using Apt-Mirror on our Ubuntu Patching Servers, which serves our Ubuntu Servers on an internal network. In building our patching server we want to ensure high availability and redundancy meanwhile comply with our firewall guidelines. For firewall rules we have to specify by IP Address and cannot use Host names. Therefore I could not use [http://archive.ubuntu.com](http://archive.ubuntu.com) due to the fact it has multiple IP's which I assume change based on what mirror is available (correct to assume?). As a result we chose several mirrors with specific IP's.  

This works fine with particular IP, but I would like to specify this list of IP's based on what is available. (ie if the first site is not available, it will choose the 2nd on the list). The files should go into the same folder to have one single local mirror. The issue I am facing is that I am only able to specify one mirror in our mirror.list file. If I have two or mirrors in the mirror.list file it creates a separate folder with that particular site's mirror(ie mirror.us.leaseweb.net/ and mirror.cc.columbia.edu/.) This is impractical since it would not only download another 30+GB but it would be in a separate location and would have to repoint all the servers to that location to pull from or create a new link.

I could not find a way to customize the naming convention of the folder. Is there some way to do this?
[TABLE]
[TR]
[TD]Name[/TD]
[TD]URL[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]LeaseWeb USA, Inc[/TD]
[TD][http://mirror.us.leaseweb.net/ubuntu/](http://mirror.us.leaseweb.net/ubuntu/)[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]Columbia University[/TD]
[TD][http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/)[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]Virginia Tech [/TD]
[TD][http://mirror.cc.vt.edu/pub2/ubuntu/](http://mirror.cc.vt.edu/pub2/ubuntu/)[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]Limestone Networks[/TD]
[TD][http://mirror.lstn.net/ubuntu/](http://mirror.lstn.net/ubuntu/)[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]Pacific NorthWest National Lab[/TD]
[TD][http://mirror.pnl.gov/ubuntu/](http://mirror.pnl.gov/ubuntu/)[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[/TABLE]

Thanks
Jason

---

### Post by jasoncal on 2014-09-08
Still no luck on my side...Any advice for this?

---

