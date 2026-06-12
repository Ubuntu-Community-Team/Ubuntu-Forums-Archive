---
title: "Please help, I'm so desperated!!!"
date: 2007-05-18
forum: General Help
---

### Post by MaestroS on 2007-05-18
Guys... I'm going really crazy ! ! !

I were trying to use this:
[http://ubuntuforums.org/showthread.php?t=434952](http://ubuntuforums.org/showthread.php?t=434952)

But it required gtk2 - but GTK2 requires more libs and more... and I can't compile it!

This **** still says that gcc cannot make executable files


How do **** do I compile it, if it WONT compile ?!?!?!?!
I want my net work on Ubuntu!

---

### Post by loathsome on 2007-05-18
Grab the build essentials.

```
sudo apt-get install build-essential
```

---

### Post by MaestroS on 2007-05-18
How do I do it if I dont have net ???

That's why I need GTK2 - to compile wireless driver :S:S:S

---

### Post by loathsome on 2007-05-18
Um, that's like asking "how do I download from the internet without a connection".

You can get a friend to download the deb-files, give them to you and then you can run them locally. This will download all required files and place them under /var/cache/apt/archives:

```

sudo apt-get clean && sudo apt-get install -d build-essential
```

edit; Ey, you're online here, aren't you?

---

### Post by Cappy on 2007-05-18
[http://packages.ubuntu.com/feisty/devel/build-essential](http://packages.ubuntu.com/feisty/devel/build-essential)
I guess you'll need those related packages too.

---

