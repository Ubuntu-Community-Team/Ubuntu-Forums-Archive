---
title: "Internet connection Problem!!"
date: 2007-01-30
forum: General Help
---

### Post by hadiriazi on 2007-01-30
Hi everyone,
Here is the problem I'm facing. When I try to connect to the Internet for the first time, if some problem appears I can't connect anymore. The thing is with the LiveCD I could connect with out any problems, but when I install ubuntu it gives me this error:

```
the interface dos not exist
```

I tried installing the following versions: 6.06 and also the DVD version but the I get the same results!!

any help will be appreciated.

---

### Post by p!=f on 2007-01-30
> **hadiriazi said:**
> Hi everyone,
Here is the problem I'm facing. When I try to connect to the Internet for the first time, if some problem appears I can't connect anymore. The thing is with the LiveCD I could connect with out any problems, but when I install ubuntu it gives me this error:

```
the interface dos not exist
```

I tried installing the following versions: 6.06 and also the DVD version but the I get the same results!!

any help will be appreciated.
Please post your /etc/network/interfaces and output of 
```

lspci | grep -i ethernet 
ip ad

```
Looks like you don't have the interface set up.

---

