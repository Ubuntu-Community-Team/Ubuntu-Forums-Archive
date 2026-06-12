---
title: "installing php"
date: 2013-01-21
forum: General Help
---

### Post by jswainst on 2013-01-21
I'm trying to install php 5.0.5 on ubuntu 12.04. How would I do that?

---

### Post by Cheesemill on 2013-01-21
You can install PHP version 5.3.10 by doing...
```
sudo apt-get install php5
```

AFAIK version 5.0.5 isn't available in the Ubuntu repositories, you would probably have to compile it yourself from source. Version 5.0.5 is also an old unsupported release, it isn't recommended to use it anymore. Is there any particular reason you *have* to have that specific version?

---

### Post by mcduck on 2013-01-21
Ubuntu's official server guide has pretty good instructions for this kind of things: [https://help.ubuntu.com/12.04/serverguide/php5.html]("https://help.ubuntu.com/12.04/serverguide/php5.html")

---

### Post by jswainst on 2013-01-21
I figured I might have to compile it myself. I'm supporting an old web site that can't run on any version past 5.0.x.

---

