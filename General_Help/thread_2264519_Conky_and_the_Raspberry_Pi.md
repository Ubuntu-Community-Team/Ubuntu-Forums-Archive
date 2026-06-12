---
title: "Conky and the Raspberry Pi"
date: 2015-02-08
forum: General Help
---

### Post by CatKiller on 2015-02-08
I've got conky set up on my desktop, and I've just got a Raspberry Pi. Is there anything neat I can pull across the network to display status information about the Pi on my desktop?

---

### Post by nerdtron on 2015-02-08
not a master of conky but I think I can share an idea.

Setup paswordless ssh between your computer and the raspberry pi. Then setup ssh commands that will query information on the raspberry pi. 

Something like:
ssh me@raspberry "free -m" > log_file.txt

Now that the log_file.txt is on your computer, I think you can use conky to display contents of a file right?

---

