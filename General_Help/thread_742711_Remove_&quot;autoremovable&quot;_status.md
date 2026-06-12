---
title: "Remove &quot;autoremovable&quot; status"
date: 2008-04-02
forum: General Help
---

### Post by yghannam7388 on 2008-04-02
Hello all,

Recently I installed OpenOffice 2.4.0 on Ubuntu 7.10 and since then a number of the OpenOffice packages are now labeled as "autoremovable." I want to know how to remove that status from them. Any help will be greatly appreciated.

Thanks,

YG

---

### Post by yghannam7388 on 2008-04-02
*bump*

---

### Post by pointone on 2008-04-02
Just manually install them: "apt-get install <packagename>".

---

### Post by yghannam7388 on 2008-04-02
Thanks for the response but OpenOffice 2.4 isn't in the repositories yet. I had to download the deb packages from the website and manually install them. I did the following:

```
sudo dpkg -i openoffice*.deb
```

and that installed everything fine. The problem is that Synaptic labels some of those packages as "autoremovable" probably because no other packages depend on them. I was wondering if there is a way to let Synaptic know that they are necessary packages.

---

