---
title: "sudo add-apt-repository ppa:diesch/testing"
date: 2012-12-21
forum: General Help
---

### Post by Holmes.Sherlock on 2012-12-21
What does the following command change to my system?
```

[COLOR=orange]sudo add-apt-repository ppa:diesch/testing[/COLOR]

```

---

### Post by Rexilion on 2012-12-21
It adds another ppa to your box. Probably just a textfile in:

/etc/apt/sources.list.d/ that points to packages and source packages of the ppa
/etc/apt/trusted.gpg.d/ that contains a key to check the signature of the packages downloaded from the ppa.

Why Sherlock? =)

---

### Post by Holmes.Sherlock on 2012-12-21
> **Rexilion said:**
> 
Why Sherlock? =)
Because this is the alias behind which I hide my cyber presence everywhere, especially [here]("http://reboot.pro/user/40460-holmessherlock/").

---

### Post by oldos2er on 2012-12-21
> **Holmes.Sherlock said:**
> What does the following command change to my system?
```

[COLOR=orange]sudo add-apt-repository ppa:diesch/testing[/COLOR]

```

```
man add-apt-repository
``` will explain in detail.

---

