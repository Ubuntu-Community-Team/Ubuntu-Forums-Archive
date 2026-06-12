---
title: "iwlist shows cached results"
date: 2005-05-10
forum: General Help
---

### Post by richbayliss on 2005-05-10
Hi,

I am working on a small project for my university. It is a web-based application to view wireless networks in an area, and view their settings.

Now, I have my USB WiFi card working through the NDISWrapper modules, and if i do a "sudo su -" and run "iwlist wlan0 scan" then I see a list of AP's available. Great! Or so I thought it was until I ran the same command as "www-data" (Apache2's user)

When I run the listing command as www-data, I still see some results, but no matter how many times I run it, I ALWAYS get the last set of results I got, when i ran it as root.

So, I altered my /etc/sudoers file and made "www-data" able to run "iwlist" as sudo with no password. This works fine, no errors, no password needed, but I still get cached results  :mad: 

So, does anybody know of a way that I can get "iwlist wlan0 scan" to be run by "www-data" (using exec() in PHP, if it matters) and get a clean set of results each time??

Thanks people, I appreciate any help.

Rich

---

