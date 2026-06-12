---
title: "&quot;Errno 24&quot; in BitTorrent"
date: 2007-07-29
forum: General Help
---

### Post by KaiserMonkey on 2007-07-29
[This Wiki]("http://wiki.theory.org/Trouble_accessing_files_-_Errno_24_(Too_many_open_files)") does a pretty good job of explaining the problem I'm having...

Basically I'm trying to download a large compilation of classical music. The number of .mp3s included (but not the size of the overall file) seems to be an issue.

I found a solution in the [OpenBSD forums]("http://www.bsdforums.org/forums/archive/index.php/t-23808.html") that suggests running ulimit in the CLI, but I'm told it's "unlimited"...

Does anyone know of a fix or a BT client that doesn't throw this error?

Thanks.

---

### Post by tbroderick on 2007-07-29
I think bittornado can deal with it. Or try editting /etc/security/limits.conf and add
```

your_username hard nofile 1024 (or whatever)

```

---

### Post by KaiserMonkey on 2007-07-31
Thanks a lot for your help =)

---

