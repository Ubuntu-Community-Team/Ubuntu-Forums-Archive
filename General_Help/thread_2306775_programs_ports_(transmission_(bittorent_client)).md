---
title: "programs ports (transmission (bittorent client))"
date: 2015-12-18
forum: General Help
---

### Post by hezy2 on 2015-12-18
Hello,
how can I know programs ports in ubuntu 15.04? Thanks,
Hezy.

---

### Post by ian-weisser on 2015-12-18
Using the 'netstat' command is one good way.

---

### Post by SeijiSensei on 2015-12-19
Registered port numbers are in the file /etc/services.  Things like bittorrent clients often use arbitrary ports > 1023 that you set in the program itself.

---

