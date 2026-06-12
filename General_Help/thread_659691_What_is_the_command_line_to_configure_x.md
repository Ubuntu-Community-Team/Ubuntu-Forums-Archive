---
title: "What is the command line to configure x?"
date: 2008-01-06
forum: General Help
---

### Post by Chamelion on 2008-01-06
I just uninstalled Nvidia driver in Gutsy because the wrong drivers where installed by Envy. Nvidia 512instead of 256mb) I now can't boot. What is the command line to reconfigure x. I knew I should not have stuffed around with this.:) Somebody please help! Thank you!!!

---

### Post by taurus on 2008-01-06
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by yabbadabbadont on 2008-01-06
```
sudo dpkg-reconfigure -p high xserver-xorg
```

Edit: Doh!  Too slow.  :lol:

---

### Post by Chamelion on 2008-01-06
Thanks heaps guys.
> sudo dpkg-reconfigure -phigh xserver-xorg
did not quite do it, but you gave my memory a jolt.:lolflag:
> # dpkg-reconfigure xserver-xorg
made it happen. Great relief here.:)

---

