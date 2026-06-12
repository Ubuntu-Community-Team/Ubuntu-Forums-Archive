---
title: "machine check exception not logged?"
date: 2008-04-10
forum: General Help
---

### Post by hsjC on 2008-04-10
I am getting this machine check exception on boot sometimes. I was prompted to use mcelog to decode the error message.

But twice this morning, I typed "sudo mcelog --core2 --ascii" and nothing happens...

/var/log/mcelog is still empty.

I even checked /dev/mcelog it's also empty before I did the above command, why is the exception not logged?

btw I'm using ubuntu hardy beta x64

---

