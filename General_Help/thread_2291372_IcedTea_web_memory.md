---
title: "IcedTea web memory"
date: 2015-08-19
forum: General Help
---

### Post by fernando54 on 2015-08-19
Hi all,
I'm running javaws (icedtea-web 1.5 (1.5-1ubuntu1)) on jnlp files which retrieve data from a server (tunneling like ssh -L8080:localhost:8080). So far it works when I have to open small-medium data, but when I retrieve bigger files and I monitor the process I see that the application is stuck at 1.6G of memory, not going further and my window is not completely loaded. I looked high and low how trying to increase that but not a clue (nothing shows at itweb-settings about that)
Of course in the jnlp fle I've included 
```
<resources>  
        <j2se version="1.6+" java-vm-args="-Xms256m -Xmx6144m -d64"/> 

```

PS: working on Ubuntu 14.04 LTS / linux 3.16.0-45-generic
with 8G memory and Intel® Core&#8482; i5-5200U CPU @ 2.20GHz × 4 

Any idea how to set a bigger memory in the process? Thanks

---

