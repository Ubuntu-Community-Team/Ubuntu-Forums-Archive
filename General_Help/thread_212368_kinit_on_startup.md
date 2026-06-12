---
title: "kinit on startup"
date: 2006-07-09
forum: General Help
---

### Post by jasonlfunk on 2006-07-09
Is there a way to get kerberos tickets when logging in, using the username and password of the user logging in?

If not, is there a way at least to get kerberos tickets on startup in general?

---

### Post by colonelk on 2006-09-06
I need an answer to this too please

---

### Post by An-Torch-a on 2007-05-07
Somebody can help us in this case?, i have the same problem, too. Please!!!!!!!! :confused:

---

### Post by Doc_symbiosis on 2007-07-25
Install the libpam-krb5 package

Add the following line to /etc/pam.d/common-password (replace similar lines):
```

password   sufficient  pam_krb5.so use_authtok
password   sufficient  pam_unix.so nullok obscure min=4 max=8 md5

```

```

auth    sufficient      pam_krb5.so forwardable
auth    required        pam_unix.so nullok_secure try_first_pass

```

This should do the trick.

---

