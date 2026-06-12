---
title: "/usr/bin/dpkg returned an error code (1)"
date: 2013-01-14
forum: General Help
---

### Post by Pedro Araujo on 2013-01-14
Hi, every time I go to install some application, I can't, because a error is generated: 

```
linux-image-3.2.0-29-generic

/usr/bin/dpkg returned an error code (1)
```

I have tried removing and installing again, but I cant remove too, because the same error is caused.

How can I fix it?

---

### Post by Impavidus on 2013-01-14
This isn't an application, it's the kernel, and not the most recent version. Why do want to install it? You probably have a more recent version installed already (in my case, 3.2.0-35). Or dpkg refuses because you're running that kernel right now.

---

### Post by ibjsb4 on 2013-01-14
What kind of output do you get with ..

```
sudo apt-get update
```

---

