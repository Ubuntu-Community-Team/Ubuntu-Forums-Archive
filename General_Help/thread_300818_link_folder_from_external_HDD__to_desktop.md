---
title: "link folder from external HDD  to desktop"
date: 2006-11-16
forum: General Help
---

### Post by patagonik on 2006-11-16
I have all my music stored in an external HDD and i would like to make a link to the desktop to avoid having to open the HDD and then open the music folder and then... Error Message: operation not permitted. I have the rights ok to write, execute, and read in both Desktop and HDD... so, why can't i do this link into the desktop?

Thanks in advance!

---

### Post by Nameless_one on 2006-11-16
What exactly did you do? 

I think you should:

```
ln -s /<path-to-HDD> ~/Desktop/<name-of-link>
```

---

### Post by patagonik on 2006-11-16
Man!!! It worked perfect! :D  Thanks a lot!!! I only right clicked in the music folder and ask nautilus to Make Link -> error... but the command line just did it!

Viva Ubuntu bordel! Merci monsieur!

pata

---

### Post by Nameless_one on 2006-11-16
No problem. The command line is your friend.

---

