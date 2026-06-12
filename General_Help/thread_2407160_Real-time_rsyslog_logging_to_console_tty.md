---
title: "Real-time rsyslog logging to console tty"
date: 2018-11-30
forum: General Help
---

### Post by contv on 2018-11-30
Hello!

I'm trying, without success, to get rsyslog to show real-time logs on tty12, any tty for that matter. I edited **/etc/rsyslog.d/50-default.conf** file, restarted rsyslog, nothing happens. Googled to no avail. What am I missing? (Ubuntu 18.04.1 LTS, rsyslog 8.32.0)

```
[COLOR=#555555]daemon,mail.*;\[/COLOR]       
news.=crit;news.=err;news.=notice;\
*.=debug;*.=info;\ [COLOR=#555555]       
*.=notice;*.=warn       /dev/tty12[/COLOR]
```

Thanks

---

### Post by SeijiSensei on 2018-11-30
Have you tried /dev/console?

---

### Post by contv on 2018-12-01
> **SeijiSensei said:**
> Have you tried /dev/console?
I did, nothing happens. :(

---

