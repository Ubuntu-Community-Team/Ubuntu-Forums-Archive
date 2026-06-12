---
title: "any ETA on riscv64 docker image?"
date: 2024-06-24
forum: General Help
---

### Post by kasperk81 on 2024-06-24
i was asking on github that `docker run --platform linux/riscv64 ubuntu:24.04` is not available and they said that official image hasn't been published by Canonical: [https://github.com/docker-library/official-images/pull/16978#issuecomment-2187003376](https://github.com/docker-library/official-images/pull/16978#issuecomment-2187003376)

any ETA on that?

alpine linux 20 supports it e.g. `docker run --rm --platform linux/riscv64 alpine:3.20 uname -a` =>
Linux a8e0efab6dd4 6.6.31-linuxkit #1 SMP Thu May 23 08:36:57 UTC 2024 riscv64 Linux`

---

### Post by TheFu on 2024-06-25
Nobody here works for Canonical.

---

### Post by kasperk81 on 2024-06-26
funny, #ubuntu on irc told me the same thing except they told me to post on this forum "which Canonical folks watch". so i guess mailing list is the only option

---

### Post by TheFu on 2024-06-26
I think Canonical all moved to Discord when the IRC blow-out happened a few years ago.

---

