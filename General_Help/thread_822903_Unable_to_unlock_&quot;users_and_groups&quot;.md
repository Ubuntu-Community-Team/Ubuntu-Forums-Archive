---
title: "Unable to unlock &quot;users and groups&quot;"
date: 2008-06-08
forum: General Help
---

### Post by anando on 2008-06-08
Hi

I am unable to 'unlock' the Users and groups administration dialogue using my password. I have checked that my password works for the synaptic manager and just about everything else including where I use sudo - but when I am prompted for a password whilst unlocking the 'users and groups', it wiggles a bit and then I am prompted for the password again. 

I wonder if somebody could help me with this ?

Thanks,
Anand.

---

### Post by ItsManaged on 2008-10-02
I have the same problem - did you find a way around this anando?

---

### Post by davidryder on 2008-10-02
Try 

```
sudo passwd root
```

And try using the password you set for root (I use the same root password as my user password).

---

