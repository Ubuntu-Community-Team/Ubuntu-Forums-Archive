---
title: "Lightening Ubuntu"
date: 2007-05-22
forum: General Help
---

### Post by ThinkBuntu on 2007-05-22
I'd like to edit my boot daemons and remove unnecessary modules to speed up my machine. In arch, this was very easy (/etc/rc.conf, bottom line has a simple list of Daemons). Where can I do this? I know it's loading all sorts of things I don't need.

---

### Post by cborga1985 on 2007-05-22
it would be easier for you to use [http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

easily installable by doing this
```
sudo apt-get install bum
```

---

### Post by cborga1985 on 2007-05-22
to top it off check out Start Up Manager [http://web.telia.com/~u88005282/sum/index.html](http://web.telia.com/~u88005282/sum/index.html)

---

### Post by der_joachim on 2007-05-24
There's also the cli option called sysv-rc-conf. It's in the repos.

---

