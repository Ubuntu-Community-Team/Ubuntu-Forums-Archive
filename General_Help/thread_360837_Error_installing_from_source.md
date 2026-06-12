---
title: "Error installing from source"
date: 2007-02-13
forum: General Help
---

### Post by syd2o2 on 2007-02-13
I have a problem when trying to install Kaffeine and klibido from source. When I try to run ./configure for kaffeine it stops at this:
```
checking for X... configure: error: Can't find X libraries. Please check your installation and add the correct paths!

```

configure for Klibido gets me to this:

```
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

```

How can I solve this?
I'll provide any additional info needed.

---

### Post by Soulxlight on 2007-02-13
Try this...

```
sudo apt-get xlibs-dev
```

---

### Post by syd2o2 on 2007-02-14
So I did that, and I got an error about qt. Then I did
sudo apt-get install libqt3-mt-dev

Now configure stops with this:

```
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

```

---

### Post by lamego on 2007-02-14
You just need to continue feeding the animal ;)
```
sudo apt-get install kdelibs4-dev
```

---

### Post by nrichmond on 2008-01-29
Well that helped me. but the first response. gave me an error but i tried
sudo apt-get install kdelibs4-dev
and it worked. thnx

---

