---
title: "SSH file transfer"
date: 2008-01-06
forum: General Help
---

### Post by joebanana on 2008-01-06
Can I transfer files through SSH terminal? I can't install grafic ssh clients or anything but I can establish ssh chanel and run commands through terminal.

---

### Post by daimaru on 2008-01-06
```
scp username@ipadresse:/path/to/source user@ipaddress2:/destination/path
```

---

### Post by stump138 on 2008-01-06
you can use the scp command.  there is information [here]("https://help.ubuntu.com/community/SSHHowto")

:) good luck

---

### Post by PokieCarlwin_is_borked on 2008-01-06
hey there!

daimaru  is not totally accurate & stump's link has enough info to really help you use it.  it helped me to remember to use "-r" w/ for a whole dir:)

---

