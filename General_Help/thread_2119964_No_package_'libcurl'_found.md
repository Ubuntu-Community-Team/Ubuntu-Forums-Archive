---
title: "No package 'libcurl' found"
date: 2013-02-25
forum: General Help
---

### Post by roberto32 on 2013-02-25
I've the problem
No package 'libcurl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables CURL_CFLAGS
and CURL_LIBS to avoid the need to call pkg-config.
I wanna install opkg and it's dependecy is libcurl I've already instaled libcurl3-deb
and nuthin same error. I've to tell opkg not to search for libcurl but  libcurl-3 but how
do I manage it? I've added this repo  deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) quantal-security main  but nuthin happend and i followed the steps you give and nuthin..

---

### Post by codemaniac on 2013-02-25
Hello roberto32,

Welcome to Ubuntuforums !!

Your post in now moved to its own thread.

Cheers!!

---

### Post by matt_symes on 2013-02-25
Hi

Can you post the output of

```
uname -a
```

This will tell us about your filing system and where the library may be.

Kind regards

---

