---
title: "Trouble booting Ubuntu after Kubuntu installation"
date: 2008-03-07
forum: General Help
---

### Post by 449 on 2008-03-07
I'm getting really good at creating problems for myself. :confused:

[http://i28.tinypic.com/15gec2f.png](http://i28.tinypic.com/15gec2f.png)

Anyways, after installing Kubuntu to sda1, I could no longer boot Ubuntu normally. It still showed up in the grub menu, I would select to boot it, it would load about a quarter of the way, and then go into terminal. Then if I pressed Ctrl + Alt + Del, it would boot the rest normally and everything is fine. **Except**, that sda6 is no where to be found. 

 sda6 *did* show up in my new Kubuntu install. I tried to "fix" it with super Grub, but all that did was make it so I can no longer boot Kubuntu(not a big deal to me because I'm planning on replacing it with Sid anyways.)

So what it's come down to now is that I can't access my sda6 partition which has all my files that I care about on. 

Oh, I think I just thought of at least, why it's not showing up. Before I had installed Kubuntu, I had Debian Lenny on sda1, sda7 was the home partition for it. I hope that helps... 

Help please?

Thanks

**Solved how to mount sda6**

---

