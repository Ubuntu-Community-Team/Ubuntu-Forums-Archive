---
title: "Security Updates"
date: 2008-04-13
forum: General Help
---

### Post by abbasali31 on 2008-04-13
Usually after the installation, if the Internet is up then ubuntu will go to the ubuntu site and downloads all the updates automatically to keep the system up to date.  This time I chose to install ubuntu through LIVE CD, and the installation went successful, but some how it didn't download any updates at all even though the Internet is up.

Am I missing something?

Thanks

---

### Post by john.nicholls on 2008-04-14
Just check (in Synaptic, for example) that the security updates repository has been selected, and then download any updates.

---

### Post by PmDematagoda on 2008-04-14
Oops, misinterpreted the OP's post, yes, do what john.nicholls suggested. You could also try reloading the sources lists with:-
```
sudo apt-get update
```

---

