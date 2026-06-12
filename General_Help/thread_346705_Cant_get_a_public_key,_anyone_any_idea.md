---
title: "Cant get a public key, anyone any idea??"
date: 2007-01-26
forum: General Help
---

### Post by mattgaunt on 2007-01-26
Heya everyone

Im just trying to install beryl on my laptop after getting it on my main computer using ubuntu. Now i am using kubuntu on my laptop and yeah it looks like KDE has alot of potential BUT i cant get a public key from the beryl repo

Now ive posted on both the beryl and kubuntu forum and no1 is given me a look, so instead i thought id try here since everyone here seems to be able to help me out

So does anyone have any idea why my public key wont download?? this is what i get from the terminal

> matt@matt-laptop:~$ wget [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg) -O- | sudo apt-key add -
--09:44:17--  [http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg](http://ubuntu.beryl-project.org/root@lupine.me.uk.gpg)
           => `-'
Resolving ubuntu.beryl-project.org... 64.15.154.150, 80.77.247.17, 88.191.250.18, ...
Connecting to ubuntu.beryl-project.org|64.15.154.150|:80... failed: Connection timed out.
Connecting to ubuntu.beryl-project.org|80.77.247.17|:80... failed: Connection timed out.
Connecting to ubuntu.beryl-project.org|88.191.250.18|:80...    

and it just doest that for 20 times and then says its giving up, so does anyone have any idea whats rong with it?? i had major problems setting it up so adept would even connect to the internet but now that seems to be fine so any help would be great

Matt

---

### Post by ranarion on 2007-01-26
Well, from what you posted here, these servers *do* seem down, don't they? Try telnetting into them on port 80 and check whether this gives you any response. If it doesn't, contact their admins about it.

---

