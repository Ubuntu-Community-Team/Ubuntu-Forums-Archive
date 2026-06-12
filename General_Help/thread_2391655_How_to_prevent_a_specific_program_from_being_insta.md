---
title: "How to prevent a specific program from being installed/updated"
date: 2018-05-11
forum: General Help
---

### Post by operator-error on 2018-05-11
The other day, the update manager installed python3-apport (along with apport and apport-kde).  I promptly removed them due to privacy concerns.  Is there a way I can block those particular programs from being installed/updated in the future (either in the terminal or through Discover)?  I'd like to be able to do a 'sudo apt-get upgrade' in the terminal and have the system automatically overlook/ignore those programs.  Thanks.

---

### Post by Dennis N on 2018-05-11
You can use 
```
sudo apt-mark hold <package-name(s)>
```
so 
```
sudo apt-mark hold python3-apport apport apport-kde
```
should work.

You can use wild cards also, so **apport*** would also hold back **apport-kde** and anything else starting with **apport**.

---

### Post by operator-error on 2018-05-11
> **Dennis N said:**
> You can use 
```
sudo apt-mark hold <package-name(s)>
```
so 
```
sudo apt-mark hold python3-apport apport apport-kde
```
should work.

You can use wild cards also, so **apport*** would also hold back **apport-kde** and anything else starting with **apport**.

Thanks for your reply.  I appreciate your help. :)

---

