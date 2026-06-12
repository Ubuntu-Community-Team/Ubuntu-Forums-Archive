---
title: "Locale issue on new 6.06 install"
date: 2007-02-28
forum: General Help
---

### Post by Koobi on 2007-02-28
Hi,

I regularly get this error:
```

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_AU:en",
        LC_ALL = (unset),
        LANG = "en_AU.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
/usr/bin/locale: Cannot set LC_ALL to default locale: No such file or directory

```


I just installed 6.06 with GUI on a generic PC which I will be using as a Desktop/Server.
I'm using Gnome, if that helps.

I'd like to use en_US.UTF-8 if possible.

Any idea how I can sort this out?


Thanks.

---

### Post by Koobi on 2007-03-01
Any suggestions, anyone please?


I tried this but it solved nothing:
```

$ cat /usr/share/i18n/SUPPORTED | grep "en\|ru" > /var/lib/locales/supported.d/local
$ dpkg-reconfigure locales
$ update-locale LANG=en_US.UTF-8

```

---

