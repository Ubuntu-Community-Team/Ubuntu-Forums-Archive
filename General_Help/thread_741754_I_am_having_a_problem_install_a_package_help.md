---
title: "I am having a problem install a package help?"
date: 2008-04-01
forum: General Help
---

### Post by adn258 on 2008-04-01
It's source code so it needs to be compiled and it is lives 0.9.8.9 video editor.  Anyway I read the install file and it's standard you use the terminal and use CD to change to the directory of the source code.  Then I type ./configure and it does it's thing but at the end of the configuration I get No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables GTK_CFLAGS
and GTK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

I get the above the terminal but it happens at the very End 

austin@bomb:~/Desktop/lives-0.9.8.9$ make
make: *** No targets specified and no makefile found.  Stop.

What should I do?

---

### Post by Sef on 2008-04-01
Did you install build-essential?

From the terminal

```
sudo apt-get update
```

```
sudo atp-get install build-essential
```

or install it from Systems > Administration > Synaptic Package Manager

---

### Post by adn258 on 2008-04-01
> **Sef said:**
> Did you install build-essential?

From the terminal

```
sudo apt-get update
```

```
sudo atp-get install build-essential
```

or install it from Systems > Administration > Synaptic Package Manager

Yes I have already done that umm?

---

