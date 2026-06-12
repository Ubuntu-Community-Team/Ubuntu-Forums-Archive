---
title: "[SOLVED] Enable status bar in vi program"
date: 2008-05-10
forum: General Help
---

### Post by abcuser on 2008-05-10
Hi,
I am used to Suse Linux where status bar in vi program is always displayed. But in Ubuntu 8.04 when vi is used there is no status bar, so I don't know if I am in insert or command mode. So, how to enable status bar in vi program?
Thanks,
Abcuser

---

### Post by Nepherte on 2008-05-10
Don't know the solution, but when I'm in insert mode vi tells me -- INSERT -- in the status bar. So I don't think it's normal behaviour. I did install the vim-full package though, perhaps that's it.

---

### Post by abcuser on 2008-05-10
Hi,
I have a default installagion of Ubuntu 8.04 and there is no status bar at all.
Regards,
Abcuser

---

### Post by Nepherte on 2008-05-10
Try installing the full vim package then and see if that helps:
```
sudo apt-get install vim-full
```

---

### Post by abcuser on 2008-05-11
Nepherte, installing vim-full package solved the problem.
Thanks a lot,
Abcuser

---

