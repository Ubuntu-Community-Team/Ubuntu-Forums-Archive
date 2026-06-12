---
title: "please help me with my acer aspire 3680"
date: 2007-12-16
forum: General Help
---

### Post by ryudo423 on 2007-12-16
hi  have a Atheros AR5006EG wireless card.....my wireless isnt working it doesnt even say enable wireless...any help would be great thank you!!

---

### Post by mathnerd314 on 2007-12-27
Have you tried enabling the wireless card driver (System --> Administration --> Restricted Drivers Manager)? That worked for me.

Edit: Actually, I just realized that although I have the same model of computer, I have a Broadcom card instead of Atheros. So I'm not sure if that would actually work or not, but you could try...

---

### Post by jken146 on 2007-12-27
First try the restricted drivers manager.  Then look at the output of **lshw** to see if there is a "driver=....." bit for your wireless card.  Then try madwifi.

---

### Post by bbqsandwich on 2008-01-08
I've also got an Acer Aspire 3680; here's a link to a post in another thread I wrote about how I got my wireless working. Hope it works for you!

[http://ubuntuforums.org/showpost.php?p=4096300&postcount=6](http://ubuntuforums.org/showpost.php?p=4096300&postcount=6)

---

