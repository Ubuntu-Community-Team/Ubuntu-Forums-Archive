---
title: "Weird problem with Synaptic and Proxy"
date: 2007-12-07
forum: General Help
---

### Post by aldav on 2007-12-07
I have the following problem, I am behind a proxy to access the Internet, but local addresses don't require a proxy. When I open Synaptic and try to install something I have the following error:

```
W: Failed to fetch http://ubuntu.prod.uci.cu/ubuntu/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-14.46_i386.deb
  407 Proxy Authentication Required
```

Then I change the Synaptic Network configuration from "Direct Internet Connection" to "Manual Proxy Configuration", I fill the information about proxy address, port, username and password. Then I retry to install and this is the error I get:

```
W: Failed to fetch http://ubuntu.prod.uci.cu/ubuntu/pool/main/l/linux-source-2.6.22/linux-libc-dev_2.6.22-14.46_i386.deb
  407 Proxy Authentication Required
```

Then I change back from "Manual Proxy Configuration" to "Direct Internet Connection" and  now the installation works fine. This happens every time I try to install something, at the end I can install it, but I have to pass through all the previous steps to achieve it.
Any clues why?

---

### Post by metalheart on 2007-12-07
After changing the proxy settings you must Refresh (Ctrl+R) the repositories.

---

### Post by aldav on 2007-12-07
Won't work. When I start Synaptic, the default Network setting is "Direct connection to the Internet", which I think is fine, 'cause I'm not using Internet repos, I'm using my college local repo, Still when I refresh the repos I get this error:

[HTML]http://ubuntu.prod.uci.cu/ubuntu/dists/feisty/multiverse/binary-i386/Packages.gz: 407 Proxy Authentication Required[/HTML]

After this I can do all the steps I mentioned in the previous post and it works in the end. But all those steps are annoying, and I don't want to do them.

---

### Post by metalheart on 2007-12-07
The problem is, that the synaptic configuration file is not updated with proxy information without reloading the repository information.

Take a look at the file in the root home directory
```
/root/.synaptic/synaptic.conf
```
There is at the end of the file option useProxy. Set it's value to "0" to turn proxy off. Then run
```
sudo apt-get update
```
Now run Synaptic

---

