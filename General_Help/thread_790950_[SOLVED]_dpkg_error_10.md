---
title: "[SOLVED] dpkg error 10"
date: 2008-05-11
forum: General Help
---

### Post by orlox on 2008-05-11
Hi! Recently on an update I started getting a dpkg error 10 when dpkg tried to configure the foomatic-filters package. Although I managed to install things and get additional updates with no trouble, this thing annoyed me, so I tried to purge the package and reinstall it...

To do this, I had to remove also the packages that depended on foomatic-filters:
[LIST]
[*]foomatic-db-engine
[*]foomatic-db-hpijs
[*]hpijs
[/LIST]
Well then I got everything removed and purged, and then proceeded to reinstall just to see the same error, only a bit worse now :(

I got the error 10 message on foomatic-filters so this package wasn't configured. As this package wasn't configured, also the other packages weren't configured cause of dependencies issues. So, I can't use my printer right now cause those packages aren't installed correctly...

Any help??

---

### Post by zvacet on 2008-05-12
```
sudo dpkg --configure -a
```

---

### Post by orlox on 2008-05-12
Did that already (synaptic directly told me to do that), but it only tries to reconfigure the packages with the same result....

---

### Post by orlox on 2008-05-18
Really need some help now T.T

The package libapache2-mod-php5 is now also giving me the error 10 message and not getting configured, so I don't have php5 wich is crucial to me..

---

### Post by orlox on 2008-05-18
Found the solution...

I was looking through the postinstallation scripts of both packages and noticed that if I commented a line that run a command called ucf, everything went fine, so I guessed there was something wrong with ucf...

thus, I went to synaptic, reinstalled ucf, and now everithing configures just fine...

---

