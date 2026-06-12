---
title: "Please Help!!  [Resolved]"
date: 2007-02-11
forum: General Help
---

### Post by skoalman88 on 2007-02-11
After following this guide [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I rebooted and now I get a "Fatal service error: no screens found" message when U type "startx" at the command prompt.

PLEASE HELP!!!!!!!!

SOLVED!!!!!!!!!!!!!!!

---

### Post by taurus on 2007-02-11
```
sudo dpkg-reconfigure xserver-xorg
startx
```

---

### Post by skoalman88 on 2007-02-11
Taurus, you are my hero. Although I am sure this was a simple fix in your eyes, you helped me avoid a major crisis. Thank you very much.

---

