---
title: "Recommended Updates Require Untrusted Packages"
date: 2013-11-27
forum: General Help
---

### Post by navneeth on 2013-11-27
Hi. I have received a few updates for the package management system. Before the installation is to start, a message pops up informing me that a bunch of untrusted packages are required. Why would recommended updates require untrusted packages? 

Screenshot attached for reference:
[ATTACH=CONFIG]248135[/ATTACH]

---

### Post by Frogs Hair on 2013-11-27
Usually running the following command resolves the problem . There have been posts about this message before and it might be related update frequency. I have only seen it once myself , but I update daily usually when I login. I prefer to smaller and more frequent updates .  ```
sudo apt-get update 
```

---

### Post by navneeth on 2013-11-27
Thanks, the command line didn't put up any warnings.

I too have the computer check for updates daily, so frequency is probably not it. Next time it shows up, I'll probably file a bug report (assuming it hasn't already been done).

---

