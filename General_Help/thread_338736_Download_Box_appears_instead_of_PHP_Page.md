---
title: "Download Box appears instead of PHP Page"
date: 2007-01-14
forum: General Help
---

### Post by Aazn on 2007-01-14
I have a general outline here, at my server. This is also partially a test to see if it works for everyone else and not just my local LAN.

If you can't, here's the problem:

> 
[center]**The Problem**[/center]

The problem I have is that when ever I view a PHP file on this server, (my Ubuntu 6.10 Edgy desktop) the "Download Box" comes up instead of the actual PHP page.

[center]**The User**[/center]

If you can solve my problem, drop me an email at my email address.

[center]**The Thanks**[/center]

Thanks to all the people that visit this site and drop me an email. Even if it is spam...


(Deparsed Link: 75.68.49.254)

Basically when ever I view one of my own PHP files, The "Download" box appears instead of the actual page. Can anyone help me with this?

---

### Post by crispy_420 on 2007-01-15
Look at guides for mythtv setup. You may not need to get mythtv working but many users reported similar problems, I know I did. Dig around those guides and you may just find your answer there.

---

### Post by jasonsp6 on 2007-01-25
It sounds like PHP is not installed or enabled.  Instead of parsing the PHP document, Apache is trying to serve you the php file.

---

### Post by phossal on 2007-01-25
The previous post is dead-on. You haven't configured apache correctly. Which version are you using? If you downloaded packages, which ones?

[Edit] I'm assuming that you *are* using apache?

---

