---
title: "(new)synpatic error message"
date: 2007-01-16
forum: General Help
---

### Post by xGutsAndGloryx on 2007-01-16
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeartwork/kdeartwork-emoticons_3.5.5-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdeartwork/kdeartwork-emoticons_3.5.5-0ubuntu1_all.deb)
  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.35 80]


what does this mean?

---

### Post by taurus on 2007-01-16
Remove the **us.** in front of all the repos in /etc/apt/sources.list.

```
gksudo gedit /etc/apt/sources.list
```

---

