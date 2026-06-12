---
title: "Command issue"
date: 2021-12-10
forum: General Help
---

### Post by peter-1984 on 2021-12-10
Hi,
How to make the command below work expectedly?

cp -r Path*name //my.remote.ip.addr/sh_path

---

### Post by Impavidus on 2021-12-10
So, what do you expect?

I see a * in the first argument, so it seems you want some filename globbing. Look up how it works. Then you use some remote network location for the destination. I don't think cp does copies over a network. scp does. If the network location is already mounted locally, it should work with cp, but that's something you only do on local networks.

---

### Post by vanadium on 2021-12-10
What do you expect from it?

---

