---
title: "Oracle Problem"
date: 2007-02-14
forum: General Help
---

### Post by vasimakhtar on 2007-02-14
Hi
I have installed oracle-xe on ubuntu 6.6 and it was working without any problem. I also upgraded ubuntu to 6.10 edgy and working o.k. I just wonder that I am suddenly not able to access my oracle-xe through web browser. I am using firefox browser. When I update in the terminal using sudo apt-get update I am getting following error:

"W: GPG error: [http://oss.oracle.com](http://oss.oracle.com) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2E2BCDBCB38A8516

Thanks in advance for any help.

---

### Post by IcemanV9 on 2007-02-20
I have the exact same problem as you have. I've finally contacted Oracle about their public key @ oss.oracle.com. They just signed the key earlier this month, but did NOT share it with the public yet. (duh!) However, here's how to resolve it ...

```
wget [http://oss.oracle.com/el4/RPM-GPG-KEY-oracle](http://oss.oracle.com/el4/RPM-GPG-KEY-oracle)
sudo apt-key add RPM-GPG-KEY-oracle
```

That's it. :)

---

### Post by pnix on 2007-02-24
I've got the same problem. Thanks IcemanV9.:)

---

