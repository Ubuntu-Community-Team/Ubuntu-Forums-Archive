---
title: "How to set Rhythmbox as default player in Streamtuner"
date: 2006-11-02
forum: General Help
---

### Post by bacsa81 on 2006-11-02
Hello!
Could someone help me how to set Rhythmbox in Streamtuner?
rhythmbox %q doens't work...
Thanks for help!
Csaba

---

### Post by bacsa81 on 2006-11-04
Nobody has a clue? :(

---

### Post by Sytone on 2006-11-20
Hi,

Try this, works for me:
rhythmbox-client --no-start --play --play-uri=%q

This will not cause a new instance to load and will play the stream once loaded. Enjoy!

---

