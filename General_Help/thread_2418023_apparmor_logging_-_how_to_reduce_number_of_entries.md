---
title: "apparmor logging - how to reduce number of entries"
date: 2019-04-30
forum: General Help
---

### Post by holiday on 2019-04-30
Apparmor is massively cluttering the kern.log with 'ALLOWED' entries. 

The /etc/apparmor/parser.conf file has a 'verbose' setting but I don't see that it refers to logging or  how to use it if it does. 

I'm noticing these are coming for libreoffice so perhaps there is a libreoffice setting? If that is possible, where would I find that configuration.

---

### Post by Rubi1200 on 2019-05-01
Seems you might not be the only one having this issue with LibreOffice logging:
[https://askubuntu.com/questions/1138397/apparmor-logging-level-skip-audit-log](https://askubuntu.com/questions/1138397/apparmor-logging-level-skip-audit-log)

Best advice I can give is take a very good look at the various documentation links here:
[https://wiki.ubuntu.com/AppArmor](https://wiki.ubuntu.com/AppArmor)

Hope this helps somehow.

---

