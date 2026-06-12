---
title: "DenyHosts: Removing valid IP"
date: 2007-02-13
forum: General Help
---

### Post by ykhun on 2007-02-13
Hi, I wonder if anyone knows the exact steps to remove a valid IP from being repeatedly added back into /etc/hosts.deny by DenyHosts v2.3.

Had check the author's mail archive, he mentioned a feature to "cleanse" IP is in the works. There are some other user tested ways, but i wonder if any1 here had something that definitely worked.

Thanks.

---

### Post by ykhun on 2007-02-14
I'd attempted the following but it didn't work. DenyHosts still adds the IP back into /etc/hosts.deny

- Stop denyhosts daemon
- Remove entry from /etc/hosts.deny
- Start denyhosts

---

### Post by ykhun on 2007-02-14
Ok i finally found a way to do it. Hope this helps any edgy server admins out there.


If a legit usr's IP is blocked, do the following:
1. Stop DH daemon. /etc/init.d/denyhosts stop
2. Remove usr's IP from /etc/hosts.deny
3. Grep DH's data directory for usr's IP. grep 'xxx.xxx.xxx.xxx' /usr/share/denyhosts/data/*
4. Here's the best part... Remove usr's IP from all the files that grep showed in step 3.
5. Start DH daemon. /etc/init.d/denyhosts start
6. Ask usr to log in now.

---

### Post by reclusivemonkey on 2007-02-14
> **ykhun said:**
> Ok i finally found a way to do it. Hope this helps any edgy server admins out there.


If a legit usr's IP is blocked, do the following:
1. Stop DH daemon. /etc/init.d/denyhosts stop
2. Remove usr's IP from /etc/hosts.deny
3. Grep DH's data directory for usr's IP. grep 'xxx.xxx.xxx.xxx' /usr/share/denyhosts/data/*
4. Here's the best part... Remove usr's IP from all the files that grep showed in step 3.
5. Start DH daemon. /etc/init.d/denyhosts start
6. Ask usr to log in now.

Have you written a script to do this?

---

### Post by ykhun on 2007-02-14
> **reclusivemonkey said:**
> Have you written a script to do this?

I wanted to do that, but the DH author mentioned that he will add it in the future DH releases. I guess i better leave it to the pro. :)

---

