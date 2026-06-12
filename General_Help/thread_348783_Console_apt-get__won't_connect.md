---
title: "Console apt-get  won't connect"
date: 2007-01-29
forum: General Help
---

### Post by ungluun on 2007-01-29
Hi,

My problem is this:

I can successfully apt-get with synaptic, but when I try to apt-get with the console (aterm) I can't connect to archive.ubuntu.com.

Has this something to do with the fact that I'm behind a proxy? (which I could enter in synaptic)

Thanks!

---

### Post by kpkeerthi on 2007-01-29
Check if /etc/apt/apt.conf has an entry for your proxy. If not just add 

```

Acquire::http::Proxy "http://<user-name>:<password>@<host-ip>:8080";

```

---

