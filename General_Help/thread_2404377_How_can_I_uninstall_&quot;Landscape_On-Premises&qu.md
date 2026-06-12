---
title: "How can I uninstall &quot;Landscape On-Premises&quot; on Ubuntu"
date: 2018-10-23
forum: General Help
---

### Post by dattl2 on 2018-10-23
Hello there,

I hope, that someone can help with this.
I installed Landscape using this 3 Steps: [https://landscape.canonical.com/set-up-on-prem](https://landscape.canonical.com/set-up-on-prem)
Now I try to get rid of it and I cannot find any solution on the internet. 

If I just use
```
sudo apt purge landscape-server-quickstart
```
or
```
sudo apt remove landscape-server-quickstart
```
to remove it and delete all the dependencies with
```
sudo apt autoremove
```
there remains a lot of stuff in the system e.g. cron-jobs and startup-services etc.

I don`t understand why there is no uninstallation documented on the cannonical website.
(I must confess sometimes I just become blind in finding things wich are obvious so please correct me if there is a uninstalltion documented.) 
Has anyone run in the same situation in the past and found a suitable solution?

Thank you for your time reading this - and for any help you can bring up to this.
- Dattl

---

