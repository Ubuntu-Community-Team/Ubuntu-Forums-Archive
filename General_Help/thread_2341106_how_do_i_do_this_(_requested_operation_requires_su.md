---
title: "how do i do this ( requested operation requires superuser privilege)"
date: 2016-10-24
forum: General Help
---

### Post by openation1 on 2016-10-24
Hello everyone I'm trying to install a package but it says requested operation requires superuser privilege what can i do?

this what im doing (dpkg -i.4kvideodownloader_4.1-1_amd64.deb
and it wont let me be install it

---

### Post by deadflowr on 2016-10-24
Add sudo, like:
```
sudo dpkg -i package-name.deb
```

---

