---
title: "[SOLVED] Screensaver Plugin"
date: 2008-05-25
forum: General Help
---

### Post by tad1073 on 2008-05-25
where can I find the screensaver plugin for compiz-fusion?

---

### Post by newbreed on 2008-05-25
might find here... [http://forum.compiz-fusion.org/showthread.php?p=56851]("http://forum.compiz-fusion.org/showthread.php?p=56851")

infact I do see it on list, enjoy

---

### Post by Forlong on 2008-05-25
You have to build it from source.

1. Install the dependencies:
```
sudo apt-get install compiz-bcop compiz-dev build-essential libtool libglu1-mesa-dev libxss-dev git-core
```

2. Get the code ```
git clone git://anongit.compiz-fusion.org/users/pafy/screensaver
```

3. Change to that folder ```
cd screensaver
```

4. ```
make
```

5. ```
make install
```

6. Restart Compiz ```
compiz
```

7. Enable/configure the plugin in ```
ccsm
```

---

### Post by newbreed on 2008-05-25
nice work Forlong, maybe you can help me out with this one.. [http://ubuntuforums.org/showthread.php?t=806192]("http://ubuntuforums.org/showthread.php?t=806192")

---

