---
title: "403 errors, workaround, repositories, proxy, firewall"
date: 2007-03-27
forum: General Help
---

### Post by itzpapalotl on 2007-03-27
Hi, I'm re-posting this in the hopes that it will generate a lead for me. I have the following problem. I work at a school,. and we have a t-1 line. There is no problem with the connection. Internet traffic is normal when it comes to standard downloads, and browsing, etc. But when I try to connect to the repositories to do some installation work, (and believe me I have a LOT of installing to do) i get nothing but 403 access forbidden errors, and can't do the whole apt-get thing. 

Specifics of sources.list as well as the errors, and my original post are here:

[http://www.ubuntuforums.org/showthread.php?t=355844](http://www.ubuntuforums.org/showthread.php?t=355844)

I have also scratched up the following facts.:
I CAN in fact connect to the sources and do an update, by lugging the server across the street to the local coffee shop and using their connection. This is useful only for testing, and not frankly a practical solution.

It's not my firewall. We normally run a hunk of garbage from Sonicwall to keep the kid's minds chaste, and to keep us spam and virus free, but I removed everything but it's DHCP service  from the equation, and still the same 403 access forbidden errors.

The IP address for our Tasman router is recognized by dshield.org, but has no flags or warnings. I'm not sure even what that means, but it was the only lead from my previous post. 

That's about all I know. Now. my question is two-fold at this point. The obvious one.. What's up with this, and how do i fix it? and the second, maybe more immediately useful one.

Is it doable in any way to use a proxy server to do an apt-get scenario? Like. Can I bounce my request through the coffee shop? I know they'd be okay with it. I can even set up a machine if need be. Not maybe an Ubunutu question in the end, but any takers?

---

### Post by itzpapalotl on 2007-03-30
Wweeeeeelllllllll........ I can't image I am the only person who had this problem. But... Sorted. 
If you have the same 403 error problem I was having, simply change all instances of http:// to ftp:// in your /etc/apt/sources.list and the problem melts away.....
Man. I wish I had known that two months ago.

---

