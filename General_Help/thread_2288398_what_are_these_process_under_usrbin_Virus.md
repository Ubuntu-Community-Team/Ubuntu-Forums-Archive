---
title: "what are these process under /usr/bin/? Virus?"
date: 2015-07-27
forum: General Help
---

### Post by actan on 2015-07-27
See attached screen shot, there are many suspicious process now, i used ps -ef | grep process_id and find they are all under /usr/bin

but I checked /usr/bin there are not there, these process are quite strange and I don't recognize them,

anyone knwo what are they and how to deal with them? My server is slow now, the load is quite high

Thanks!

---

### Post by kerry_s on 2015-07-27
that would be systemd, look in /var/log/* you'll see the process's get assigned numbers/letters like that.

---

