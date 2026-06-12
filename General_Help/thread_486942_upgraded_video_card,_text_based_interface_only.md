---
title: "upgraded video card, text based interface only?"
date: 2007-06-28
forum: General Help
---

### Post by tribeca26 on 2007-06-28
I recently upgraded my videocard from a Radeon 7000(PCI) (I know...) to a 7900gs.(PCI-E) When I tried to boot into Ubuntu the loading screen comes up then goes to a text based interface that tells me that it cannot find the ATI card... and it lets me log in, but its all text :/ How do I get it to recognize my new videocard? Thanks in advance!

---

### Post by speaker219 on 2007-06-28
reconfigure xserver:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by tribeca26 on 2007-06-28
thnak you! I knew it would be easy but I'm a noob, thanks!

---

### Post by speaker219 on 2007-06-28
no problem =)
let us know if it works

---

