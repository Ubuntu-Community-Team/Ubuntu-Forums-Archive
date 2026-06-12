---
title: "weird internet problem"
date: 2008-04-19
forum: General Help
---

### Post by sefaklc on 2008-04-19
hello ,
i have a wired adsl internet connection, i am using ubuntu 6.10 .I decided to update it.But synaptic doesn't work.
When i call `sudo apt-get update` from commandline , it hangs like :
```

0% [Connecting to us.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubun]

```

At first , i thought that the problem is about synaptic.Because i can use firefox , ( so i thought that i had connection ) , Then i try ssh connection , it also failed. 

What do you think about problem?
Thanks to all.

---

### Post by ryanhaigh on 2008-04-19
Based on the fact that you are getting 1.0.0.0 for the ip address of us.archive.ubuntu.com I would say either you, your isp or someone else has messed with dns settings.

---

### Post by sefaklc on 2008-04-19
ok .  I changed the dns addresses in /etc/resolv.conf with 208.67.222.222 and 208.67.220.220 [open dns] and it worked.
Thanks again

---

### Post by ryanhaigh on 2008-04-19
Happy to be of assistance. Can you please mark this thread as solved using thread tools in the top right.

---

