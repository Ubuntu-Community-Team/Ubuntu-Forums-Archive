---
title: "Perl question"
date: 2005-08-27
forum: General Help
---

### Post by KageKeeper on 2005-08-27
This isn't really a problem as it has no noticeable deterimental effects, but it bugs me....

If I am in a terminal and I am doing things, often times I get: 

```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
``` 

Anyway to make that go away?

Like I said, does not actually make things not work, I would just like to not see it. :)

Thanks!

---

### Post by arnieboy on 2005-08-27
[QUOTE=KageKeeper]This isn't really a problem as it has no noticeable deterimental effects, but it bugs me....

If I am in a terminal and I am doing things, often times I get: 

```
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en",
        LC_ALL = (unset),
        LANG = "en"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
``` 

Anyway to make that go away?

Like I said, does not actually make things not work, I would just like to not see it. :)



Thanks![/QUOTE]

do a:
```
sudo apt-get install locales liblocale-gettext-perl
```

---

### Post by KageKeeper on 2005-08-27
[QUOTE=arnieboy]do a:
```
sudo apt-get install locales liblocale-gettext-perl
```[/QUOTE]


```
locales is already the newest version.
liblocale-gettext-perl is already the newest version.
``` 

Now what? :)

---

### Post by arnieboy on 2005-08-27
[QUOTE=KageKeeper]```
locales is already the newest version.
liblocale-gettext-perl is already the newest version.
``` 

Now what? :)[/QUOTE]
"LC_ALL=C ; export LC_ALL" should do the trick for u. try it.

---

### Post by KageKeeper on 2005-08-27
[QUOTE=arnieboy]"LC_ALL=C ; export LC_ALL" should do the trick for u. try it.[/QUOTE]

All right.

Now, do I need to put that in something to make sure it is always set?

---

### Post by arnieboy on 2005-08-27
[QUOTE=KageKeeper]All right.

Now, do I need to put that in something to make sure it is always set?[/QUOTE]
try saving it in $HOME/.bashrc

---

