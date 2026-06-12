---
title: "Remmina: suddenly missing library &quot;libappindicator3.so.1&quot;"
date: 2024-05-21
forum: General Help
---

### Post by matteo-dagord on 2024-05-21
Hi,
I have been using Remmina on my notebook with Ubuntu 20.04 for several months. Specifically, I am using the latest version installed via snap.
The last time I used it was last night without any issues.

However, today I am getting the following error:
**/snap/remmina/6547/usr/bin/remmina: error while loading shared libraries: libappindicator3.so.1: cannot open shared object file: No such file or directory**

But nothing has changed since yesterday, at least as far as I know: I haven't installed any new programs and I haven't modified anything in my setup. The problem appeared for no apparent reason.
As suggested on other forums (but not related to Remmina), I tried to install the **libappindicator3-1** and **libayatana-appindicator3** packages via apt-get, but they are already installed.
I tried to force reinstall using the **--reinstall **flag, but nothing changes.
But the file is actually installed as **/usr/lib/x86_64-linux-gnu/libappindicator3.so.1**

In short, I don't know what to do and I can't even understand what happened!

---

### Post by ActionParsnip on 2024-05-21
What is the output of:
```

sudo updatedb; lsb_release -a; uname -a; locate -i libappindicator3*

```
Thanks

---

### Post by jaroslavholecek on 2024-05-23
I have the same issue on Ubuntu 22.04:
sudo updatedb; lsb_release -a; uname -a; locate -i libappindicator3*
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.4 LTS
Release:    22.04
Codename:    jammy
Linux JaHol 6.5.0-35-generic #35~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Tue May  7 09:00:52 UTC 2 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by matteo-dagord on 2024-05-23
> **ActionParsnip said:**
> What is the output of:
```

sudo updatedb; lsb_release -a; uname -a; locate -i libappindicator3*

```
Thanks

Hello,
my output
```

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 20.04.6 LTS
Release:    20.04
Codename:    focal
Linux Saturnus 5.15.0-107-generic #117~20.04.1-Ubuntu SMP Tue Apr 30 10:35:57 UTC 2024 x86_64 x86_64 x86_64 GNU/Linux

```

But in the meanwhile I tried asking ChatGPT for help :P and its suggestion was the most straightforward:
```

sudo snap remove remmina
sudo snap install remmina

```

This made Remmina work again! Hope this helps!
The mystery remains (for me) on how the error originated...

---

