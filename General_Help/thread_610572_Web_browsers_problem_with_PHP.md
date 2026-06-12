---
title: "Web browsers problem with PHP"
date: 2007-11-12
forum: General Help
---

### Post by Ferio on 2007-11-12
When I try to post something in my blog or any PHP-powered site, my browsers (Firefox, Firefox 3.0, Opera...) don't do it, but they ask me to download index.php (Firefoxes behaviour) or just don't find it (Opera). It's not a problem of my ISP, I can post from other computers that use it. This happens (among many other things) since I upgraded to Gutsy, and it happens in a clean installation too. Think I will stick to LTS releases from now on.

---

### Post by constrictor on 2007-11-12
It's nothing to do with your browser. It's the webserver on which index.php resides. PHP is a server side scripting language and hence doesn't do much with your browser except maybe set cookies and such. 

In response to your problem you might want to contact your web hosts and find out if there's a problem with their PHP processing engine.

Good luck

---

### Post by Ferio on 2007-11-12
Oh, yeah, I forgot to mention that it's not a problem of my hosting or the server (I contacted them as my first option). In fact, as I said before, it works if I post from other computers, but not from this one, and it's been happening since the very first moment I upgraded to Gutsy, but not before. I know it's weird, but that's the way it is :S

---

