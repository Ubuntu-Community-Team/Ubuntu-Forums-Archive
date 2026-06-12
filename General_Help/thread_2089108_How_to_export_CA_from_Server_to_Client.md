---
title: "How to export CA from Server to Client?"
date: 2012-11-28
forum: General Help
---

### Post by borjamf on 2012-11-28
Hi, 

Im trying to connect LDAP over StartTLS with Self-Signed CA created with Certtools following the guides step by step, but there's something wrong on the Client:
```
ldapsearch -x -H 172.25.80.144 -ZZ -b dc=prueba,dc=borja 
ldap_start_tls: Connect error (-11)
additional info: TLS: hostname does not match CN in peer certificate

```

I've realized that I need to export my CA on 12.04 Server to the Client, and I think that the problem will be fixed. 

Here is it: I really dont know how to do that. I can't make myself clear about it after some readings. Could anybody tell me how to do that?

Thanks, I know that it's a noob question.

---

### Post by luvshines on 2012-12-04
> **borjamf said:**
>  
ldap_start_tls: Connect error (-11)
additional info: TLS: hostname does not match CN in peer certificate


The error itself is explanatory, your certificate has been created with some other name than the one you are using in your ldapsearch query.
Generally, it's the FQDN or the short name of the ldap server. Check the name for which certificate has been issued and try again

---

### Post by borjamf on 2012-12-04
I've done a exhaustive check of the host config and re-created the CA. All OK.

After some tries, I've realized that there was something wrong resolving the IP/DNS.

I think that the issue is due to Virtual Machine. 

Thanks!

---

