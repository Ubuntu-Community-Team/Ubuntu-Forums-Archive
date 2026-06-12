---
title: "A couple compiling questions"
date: 2006-11-29
forum: General Help
---

### Post by Peepsalot on 2006-11-29
For some reason compiling from source has always confused me.  I think that normally a person would say to do something like ```
./configure
make
make install
```
First question:  Which of these commands should be called with sudo?

But I heard that for debian based distros, there is something called checkinstall that you should use instead.
So with checkinstall, would you just say```

./configure
sudo checkinstall

```
?

Can anyone explain what the difference is in using checkinstall?  Does it hurt to do it the old fashioned way?

---

### Post by taurus on 2006-11-29
The first two commands, ./configure && make, can run by anybody.  But the last command, make install or checkinstall, need to be ran by root since you are actually installing that to the system.  Therefore, it would look something like this when you build something from source.

```

./configure
make
sudo make install
-or-
sudo checkinstall

```

---

### Post by Peepsalot on 2006-11-29
Ok, but what difference will it make whether I choose checkinstall or make install.

---

### Post by taurus on 2006-11-29
If you install something with "sudo make install", then when it comes time to remove it, you need to download the same source and remove it by hand with "sudo make uninstall".  But if you install it with checkinstall, then you can use dpkg or even apt-get to remove it.  No need to have the original source around anymore before you can remove the binary...

That's why it's up to you which command you want to use.

---

