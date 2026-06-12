---
title: "Different time zones for different users"
date: 2006-10-23
forum: General Help
---

### Post by krage on 2006-10-23
I have a computer as work as a server, mostly as a place some friends of my is running screen with irssi, vim and have a test area for php.

But, not all of thise people are in the same time zone, is there anyway to let them have there local time on the computer?

---

### Post by metalheart on 2006-10-23
Add following line to your user(s) .bashrc script. Replace America/New_York with appropriate location.

```
export TZ=America/New_York
```

---

