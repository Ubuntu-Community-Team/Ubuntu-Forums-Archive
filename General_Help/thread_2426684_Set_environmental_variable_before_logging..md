---
title: "Set environmental variable before logging."
date: 2019-09-12
forum: General Help
---

### Post by BeniaminK on 2019-09-12
Hello,

I have a custom session, that is built with shared libs from  ```
/opt/local/libs
```. It works fine as long as there is share dlibrary  location in ```
LD_LIBRARY_PATH
``` set. In my "```
/etc/gdm3/PreSession/Default
```" I  added: '```
export LD_LIBRARY_PATH="*/opt/local/lib/*:$LD_LIBRARY_PATH
```"', but still this session doesn't run and closes with error:

```
Sep 12 10:19:05 AMDC3695 /usr/lib/gdm3/gdm-x-session[3796]: awesome:  error while loading shared libraries: libxcb-errors.so.0: cannot open  shared object file: No such file or directory
```

so it looks like LD_LIBRARY_PATH is not visible during running na gdm-x-session... it'[COLOR=#668866]s[/COLOR] not set by PreSession/Default script...

How can I set environmental variable during logging?

---

### Post by TheFu on 2019-09-12
/etc/ld.so.conf.d/ has examples you can follow.

---

### Post by HermanAB on 2019-09-13
If all else fails, put the export statements in rc.local

---

