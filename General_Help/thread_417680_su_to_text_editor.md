---
title: "su to text editor"
date: 2007-04-21
forum: General Help
---

### Post by chromesky on 2007-04-21
how, from the command line, could i run text editor as root (e.g. in order to change the apt-get lists)? i'm sure its here but my search hacking is amateur to say the least. any help wld warrant thx.

---

### Post by mhansen on 2007-04-21
sudo <text editor of choice> <file to be edited>


I prefer pico, so it's sudo pico sources.list, for example



Regards,
Mike

---

### Post by dualscreenman on 2007-04-21
$sudo <name of your text editor here, with no "<>"'s>

Give the password and you should be in.

---

