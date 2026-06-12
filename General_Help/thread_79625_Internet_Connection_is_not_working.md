---
title: "Internet Connection is not working"
date: 2005-10-20
forum: General Help
---

### Post by Leshrac on 2005-10-20
I have a computer with ubuntu 5.10 installed, it used to work flawlessly at home, even the wireless card (wich I had some trouble getting to work with ndiswrapper) worked.

But now I have moved the Computer to a new flat, the router that provides us the internet connection is a d-link one (the one at my home was a zyxel).

Now, the problem is very strange, it seems to work very well, I can connect to the wireless network and get my ip through dhcp without any trouble. But when I try to open a webpage it just opens a bit of it, or nothing at all, and stays there, loading the webpage forever. Nothing regarding the internet connection seems to work, I tried to apt for updates but it stays there loading forever too. The problem persists even if I use an ethernet cable to connect to the router.
I can use nslookup and the dns server returns valid ips, I don't understand what's happening.

Strange thing is that it works very well with windows, this might indicate that it is not a problem with the router, but knowing that it used to work with my original router.

I tried reinstalling several times but nothing did work, I no longer know what to do. any ideas?

Thank you.

---

### Post by ymmotrojam on 2005-10-20
verify that dns is set up... that's the only thing I can think of...

System>Administrate>Networking...

dns tab...

Hope that helps :)

---

### Post by Leshrac on 2005-10-22
Nope, as I stated on my first post, dns works properly.

Also, I'd like to note that the wireless connection "works" only when in open mode, it does not work with WPE enabled.

I starting to get desperate on this...

---

