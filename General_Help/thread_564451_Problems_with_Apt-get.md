---
title: "Problems with Apt-get"
date: 2007-10-01
forum: General Help
---

### Post by brodtgaard on 2007-10-01
I'm a relativly new linux-user. I use Feisty Fawn. When I install programs with Apt-get (or aptitude) I get the error:

"Errors were encountered while processing:
cpad-kernel-source
wacom-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)"

It also says that:
Warning: kernel headers don't match running Linux version.

I tried to update the kernel headers, but that wouldn't help.

Here is a link to the log (some of it in danish):
[http://www.allerkjeldsen.dk/linux/log.txt](http://www.allerkjeldsen.dk/linux/log.txt)

Got any ideas ?

---

### Post by por100pre1 on 2007-10-01
Try this:

```
sudo apt-get install -f
```

you can also try this:

```
sudo dpkg --configure -a
```

BTW, welcome to the forums!

---

