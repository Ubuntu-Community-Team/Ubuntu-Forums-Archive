---
title: "Malfunctionning of InetAddress.getLocalHost() in openjdk-8-jdk"
date: 2017-04-27
forum: General Help
---

### Post by nopenop on 2017-04-27
Hello,

I absolutely don't know where it is the most appropriate to post this issue but I'll do it here for now.

My problem is simple with openjdk-8-jdk package when I use the following code ```
InetAddress.getLocalHost()
``` I do not get a valid response, I get ```
azery-VirtualBox/127.0.1.1
``` which is not a valid IP (for information the same code works on windows).

My environment:
```
openjdk version "1.8.0_121"
OpenJDK Runtime Environment (build 1.8.0_121-8u121-b13-0ubuntu1.16.04.2-b13)
OpenJDK 64-Bit Server VM (build 25.121-b13, mixed mode)

```

A Xubuntu install
```
Linux azerty-VirtualBox 4.4.0-75-generic #96-Ubuntu SMP Thu Apr 20 09:56:33 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

Thanks for your time.

nopenop

---

