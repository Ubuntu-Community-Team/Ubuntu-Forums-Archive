---
title: "Apache &amp; invisible rewrites"
date: 2007-11-19
forum: General Help
---

### Post by MrCrussell on 2007-11-19
[turns out it was an oddity of using the default configuration, when I added a new virtual server everything sorted itself out ... who knew?]

Hey all,

I recently set up a desktop server using Gutsy and installed PHP + Apache. I've been doing some dev work on my laptop and chucking it across to the server for testing etc.

All's been going well until today ... I've been using .htaccess to rewrite URLs and today I noticed that the rewrites weren't working (probably haven't done since setup).

This is a problem and I've also noticed that if I drop php or html files into the document root of the server then attempt to access without specifying a file extension, the ***** files are served as if everything was OK.

I'm assuming some rewriting is taking place somewhere but I have no idea where and it;s driving me crazy...

Example: create a file in the documentroot called qwerty.php then attempt to access [http://192.168.1.3/qwerty](http://192.168.1.3/qwerty) - file is processed and appears.

Anyone have any clues what's causing this behaviour? PHP version is 5.2.1, Apache is 2.2.3

TIA

MrC

---

