---
title: "W32codec For Kubuntu"
date: 2007-11-06
forum: General Help
---

### Post by highboy on 2007-11-06
I've just installed Kubuntu and I've been trying to follow the process outlined for Ubuntu in the General Help section of these forums but nothing is working. I'm new to Debian. Can anyone help me get the W32codec installed?

---

### Post by Maestro23 on 2007-11-06
> **highboy said:**
> I've just installed Kubuntu and I've been trying to follow the process outlined for Ubuntu in the General Help section of these forums but nothing is working. I'm new to Debian. Can anyone help me get the W32codec installed?

Restricted Formats: [https://help.ubuntu.com/community/RestrictedFormats?highlight=%28Restricted%29%7C%28Formats%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28Restricted%29%7C%28Formats%29)

---

### Post by highboy on 2007-11-06
Those links didn't provide a method of installing the w32codec for kubuntu. I'm not new to linux, I'm new to kubuntu/ubuntu. I tried downloading the codec (rpm file) but the Konsole told me it can't install rpm files.

---

### Post by Mithrilhall on 2007-11-06
[http://www.google.com/search?q=ubuntu+w32codec&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=ubuntu+w32codec&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by forestpixie on 2007-11-06
> told me it can't install rpm files you need alien to do that

```
sudo apt-get install alien
```

from what I remember 

```
sudo alien nameof.rpm
```

will convert it to a deb package as default

---

