---
title: "gksu nautilas is not loading"
date: 2017-07-26
forum: General Help
---

### Post by l6griffin on 2017-07-26
When I try and bring up ```
gksu nautilas
``` I'm getting the error msg ```
"Unable to locate theme engine in module_path: "hcengine"
```, I did a search but all the answer come up Italian and for versions earlier than 17.04. Appreciate your help.

thanks larry

---

### Post by DuckHook on 2017-07-26
gksu has been deprecated in Ubuntu for some time now.  It is no longer supported for either nautilus or gedit. The new method for invoking root nautilus or root gedit is to use pkexec. However, pkexec does not come with policykit profiles for nautilus or gedit by default. To install them, do:```
sudo apt install nautilus-admin
```then:```
pkexec nautilus
```
BTW, it bears mentioning that invoking nautilus in root mode is playing with fire and you really should not do so unless you really know what you are doing. You could hose your whole install by playing around indiscriminately.

It should be further noted that your command is wrong. nautilus is spelled with a 'u', not an 'a'. Perhaps this is also why you get wonky results.

---

### Post by l6griffin on 2017-07-26
Thanks that solved the problem with nautilas. Unfortunately didn't get done what I needed will have to post what I'm trying to do.

---

### Post by DuckHook on 2017-07-26
> **l6griffin said:**
> …I…will have to post what I'm trying to do.We're here to help. It's best to post your underlying issue on a separate thread.

---

