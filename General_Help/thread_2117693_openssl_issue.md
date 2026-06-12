---
title: "openssl issue"
date: 2013-02-19
forum: General Help
---

### Post by dolevo on 2013-02-19
Hi all,

I am new to Linux and having an error during the openembedded project compilation. Here is the error:

```

| make[3]: Entering directory `/home/job/.../ccgost'
| /usr/bin/ld: error: cannot open openssl.ld: No such file or directory
| /usr/bin/ld: fatal error: unable to parse version script file openssl.ld
| collect2: ld returned 1 exit status
| make[3]: *** [link_o.gnu] Error 1
| make[3]: Leaving directory `/home/job/.../ccgost'

```I have checked the openssl in synaptic and it has already been installed. Also libssl-dev and some others as well. Could you please help me to figure this out? 

Thanks.

---

### Post by slickymaster on 2013-02-19
Have you confirmed that **openssl.ld** script exist in the build tree?

---

### Post by dolevo on 2013-02-19
> **slickymaster said:**
> Have you confirmed that **openssl.ld** script exist in the build tree?
I have just searched for it and found two copies. 
1. .../x86_64-linux/openssl-native-1.0.0d-r14.0/openssl-1.0.0d/engines/openssl.ld
2. .../x86_64-linux/openssl-native-1.0.0d-r14.0/openssl.ld

---

### Post by slickymaster on 2013-02-19
Yes, and that is correct. You have to have one in the root of openssl source folder and one in the engines folder.

---

### Post by dolevo on 2013-02-19
> **slickymaster said:**
> Yes, and that is correct. You have to have one in the root of openssl source folder and one in the engines folder.

What would you suggest me to do?

---

### Post by slickymaster on 2013-02-19
Try to recheck your paths and targets to confirm that everything checks out ok.

Other than that, sincerely I ran out of ideas.

---

### Post by dolevo on 2013-02-19
> **slickymaster said:**
> Try to recheck your paths and targets to confirm that everything checks out ok.

Other than that, sincerely I ran out of ideas.

I will do. Thank you.

---

