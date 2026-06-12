---
title: "apache(?) problem"
date: 2007-12-10
forum: General Help
---

### Post by godfrey on 2007-12-10
Edit: Okay, problem solved, it's a router problem. [http://mail-archives.apache.org/mod_mbox/httpd-users/200501.mbox/%3CBE749DDA-6624-11D9-8A6C-000A957B11AC@patsblacktown.nsw.edu.au%3E](http://mail-archives.apache.org/mod_mbox/httpd-users/200501.mbox/%3CBE749DDA-6624-11D9-8A6C-000A957B11AC@patsblacktown.nsw.edu.au%3E) (Though I am still not sure why 81 works)


Hi there,
I used to run apache1.3 with debian and today i just installed apache 2 + ubuntu (default apt-get installation) and i just ran into a problem.

My server:
LAN IP: 192.168.0.10
Listening 80, 81 (81 is opened for debugging this problem)
address: godfrey.no-ip.com

Within my lan:

I could access:
- [http://192.168.0.10(:80](http://192.168.0.10(:80))
- [http://192.168.0.10:81](http://192.168.0.10:81)
- [http://godfrey.no-ip.com:81](http://godfrey.no-ip.com:81)

I could not access:
- [http://godfrey.no-ip.com(:80](http://godfrey.no-ip.com(:80)) -> time out

Outside my lan, my friend could access: (feel free to try it)
- [http://godfrey.no-ip.com(:80](http://godfrey.no-ip.com(:80))
- [http://godfrey.no-ip.com:81](http://godfrey.no-ip.com:81)

The problem is, obviously, I could not access my webserver @ port 80 within my lan.. while it works perfectly well outside my lan (from what I'm told).

Also, when I access my server within my lan, I get something like:

Index of /
...(blah)...

Which turns out to be the listing of /var/www/, which contains a folder called apache2-default and that folder contains an index.htm (or html?) that shows:

It works!

However, when accessed outside my lan, instead of seeing the directory listing of /var/www, my friends told me that they see the "It works!" page directly... which kinda confused me.

Since I'm relatively new to apache(2).. I'm not really sure if this is a config problem in apache or ubuntu or my router.. any clue? Thanks in advance!

---

### Post by matthewcraig on 2007-12-11
Would use the Thread Tools menu and mark the thread Solved ?  Thx!

---

