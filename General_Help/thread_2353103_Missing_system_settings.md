---
title: "Missing system settings"
date: 2017-02-18
forum: General Help
---

### Post by wbrb on 2017-02-18
I've installed Ubuntu 16.10 Desktop amd64 and I'm missing all the system settings menus. I'm not sure if this is something I did myself while installing steam or a bad ISO download or what. When I click system settings in the top right menu nothing happens.

How does one restore default system setting functionality?

---

### Post by wbrb on 2017-02-18
Sorry for the unnecessary thread, I found [https://ubuntuforums.org/showthread.php?t=2353103]("https://ubuntuforums.org/showthread.php?t=2353103") and it solved my problem between:

```
sudo apt-get install ubuntu-desktop
```
and
```
sudo apt-get install unity-control-center
```

No clue how this was missing.

---

