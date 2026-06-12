---
title: "Firefox blocks any site"
date: 2020-05-24
forum: General Help
---

### Post by jayhawker2 on 2020-05-24
Please, just installed in an old computer Ubuntu 2011/04. How to fix Firefox so that I can browse the net?

---

### Post by howefield on 2020-05-24
> **jayhawker2 said:**
> ...Ubuntu 2011/04...

What exactly is this ?

---

### Post by 1clue on 2020-05-24
I'm thinking 11.04.

If that's the case then there's a switch to systemd between then and now. I think the easiest route would be to backup /home, reinstall a variant of the latest, maybe xubuntu or lubuntu

Then mount your backup and cherry pick files from it to restore to the new /home.

---

### Post by grahammechanical on 2020-05-24
If the OS is indeed Ubuntu 11.04 then Firefox would be at version 3.6. That version of Firefox should load web sites coded with HTML 4 but many websites would have moved on from HTML 4 to HTML 5 and beyond.

The firefox in Ubuntu 11.04 would not be able to read the markup language that many present day websites are coded with. A web browser can be backwards compatible but not forwards compatible. 

Regards

---

### Post by 1clue on 2020-05-24
Not sure if this applies yet but it could also be related to ciphers supported by the browser. 

Almost every site these days is https. Each browser has a collection of ciphers it knows. Each website has ciphers it supports. When you go to a site the browser tells the site which ciphers it knows,and the site shares the ones it accepts. 

The ciphers that are known to be compromised are blacklisted from websites (meaning up-to-date websites won't accept those ciphers) and browsers are released with new ones.

If the browser is old enough it won't have ciphers that are acceptable to the web server and the handshake fails.

---

