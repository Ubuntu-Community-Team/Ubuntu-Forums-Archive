---
title: "Try to su to root which normally works - now i get 'module is unknown'"
date: 2016-09-18
forum: General Help
---

### Post by ks0ft on 2016-09-18
I've been jacking around with some of the configurations on my 16.04 setup and now I can't su - into root
```



jeremy@jupiter:~$ su -
Password:
su: Module is unknown
jeremy@jupiter:~$



```

Any leads mightily appreciated.  I will be here to post any relevant information requested.

---

### Post by ks0ft on 2016-09-18
I found the issue in /var/log/auth.log, had to do with an old reference to google authenticator
> 
Sep 18 11:17:01 jupiter CRON[4501]: PAM adding faulty module: pam_google_authenticator.so
Sep 18 11:39:01 jupiter CRON[4526]: PAM unable to dlopen(pam_google_authenticator.so): /lib/security/pam_google_authenticator.so: cannot open shared object file: No such file or directory


---

### Post by Habitual on 2016-09-18
+1

---

