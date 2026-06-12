---
title: "Laptop switched off during upgrade"
date: 2014-02-20
forum: General Help
---

### Post by nikki4 on 2014-02-20
No idea about any of this stuff! I was installing an upgrade yesterday and didn't realise it was going to take so long (said 20 hours guessing because I haven't done one in so long) so extremely stupidly decided just to switch it off by the power button and switched it on today and it won't open properly. It says loading and then opens up to a black screen with white writing and won't go past there. After a few tries I was able to get to the recovery bit and selected the recovery option but it just stuck at a black screen with a white line flashing on top left. Can anyone help?

---

### Post by ibjsb4 on 2014-02-21
Can you get to terminal (Ctrl + Alt + T) or console (Ctrl + Alt + F1)?  If so, you can try:

```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

