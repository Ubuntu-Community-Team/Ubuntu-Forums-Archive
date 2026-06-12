---
title: "Disable Ethernet?"
date: 2012-10-16
forum: General Help
---

### Post by Deucalion29710 on 2012-10-16
I am using a tethered connection.  I would like to disable the ethernet port so that the notification will stop popping up, for I don't have cable or dsl, and I refuse to get suckered into a satellite contract.  When I go into my network settings the "options" button does not work.  How do I fix this and disable the wired ethernet option?

---

### Post by mikewhatever on 2012-10-16
You could try 'sudo ifconfig eth0 down'.

---

### Post by pqwoerituytrueiwoq on 2012-10-16
there should also be a option in your bios for this

---

### Post by Deucalion29710 on 2012-10-17
> **mikewhatever said:**
> You could try 'sudo ifconfig eth0 down'.

Is there a way to reverse this action if I need to?

---

### Post by pqwoerituytrueiwoq on 2012-10-17
```
sudo ifconfig eth0 up
```
rebooting would do it also

---

### Post by Deucalion29710 on 2012-10-17
Awesome.  Thanks.

---

