---
title: "update manager"
date: 2007-10-06
forum: General Help
---

### Post by oneloveone on 2007-10-06
Hello everyone,
When I use the update manager I get an error message that says the following.

E: clvm: subprocess post-installation script returned error exit status 3
E: redhat-cluster-suite: dependency problems - leaving unconfigured
E: system-config-cluster: dependency problems - leaving unconfigured

Do you know how to stop this problem.

Thanks

---

### Post by gavinjb on 2007-10-06
From the error message it looks like you have tried to install some software without having the dependencies available.

Have you tried to install anything recently through apt-get / synaptic that has failed to install, as I remember having a similar error once when this happened to me, when I went into Synaptic to install some software the next time I got a message with a command I had to enter in the console which fixed the problem.

---

### Post by oneloveone on 2007-10-06
I am only using supported ubuntu applications and I get this pop up with everything I try to install with the Add/Remove Applications.

Thanks

---

### Post by zvacet on 2007-10-06
**applications<accessories<terminal**

```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by oneloveone on 2007-10-07
Thanks for the script but I still have the same problem.

Thanks

---

### Post by DagMan on 2007-10-07
I've never encountered those errors myself, however if there are unmet dependencies as suggested by gavinjb then 
sudo apt-get install -f 
usually fixes it for me.

---

