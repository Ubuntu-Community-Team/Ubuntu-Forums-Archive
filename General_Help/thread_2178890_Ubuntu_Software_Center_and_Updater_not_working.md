---
title: "Ubuntu Software Center and Updater not working"
date: 2013-10-05
forum: General Help
---

### Post by nisargshah on 2013-10-05
[TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: postcell"]I'm using Ubuntu 13.04 Gnome 64-bit. The problem started when  I downloaded and installed Clam AV packages (clamav and clamav-daemon).  After that when I tried to remove them some problem occurred and now I  can neither install new software (not even through apt-get) nor install  updates. Below are the links to some screenshots regarding the error -

  [Screenshot 1]("https://docs.google.com/file/d/0B-TyP4sP9s_feTllUlpHTUNPd2M/edit?usp=sharing")

  [Screenshot 2]("https://docs.google.com/file/d/0B-TyP4sP9s_fcGpjcjlMUmRJV3M/edit?usp=sharing")
      

[/TD]
[/TR]
[/TABLE]

---

### Post by slickymaster on 2013-10-05
What those screenshots errors basically say is that the file(s) is corrupted. So remove those files and repopulate (apt-get update) them to see if that fixes the issue:```
sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
```

---

### Post by nisargshah on 2013-10-05
Thanks! It worked!

---

