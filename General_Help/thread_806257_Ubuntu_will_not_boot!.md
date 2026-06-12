---
title: "Ubuntu will not boot!"
date: 2008-05-24
forum: General Help
---

### Post by Crope on 2008-05-24
After installing Bootchart (I've been trying to lower my horrendous boot time of 1:22), Ubuntu refuses to boot. It gives me the error:

```
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

The only thing I've done before this was add "Profile" to the end of my Kernel, which was supposed to make it boot faster, and it worked like that for a long time. It wasnt until I installed Bootchart that my computer wouldn't boot.

Please help! I need my computer!

---

### Post by pointone on 2008-05-24
Does recovery mode still work?

Also, are you saying you added profile permanently to the kernel boot options? That would probably explain the long boot time. The profile option tells the system to profile the boot process, which will speed up subsequent boots, but make the profiled boot much, much slower as it examines everything. You should only use the profile boot option once, then remove it from the prompt.

---

### Post by Crope on 2008-05-24
No, recovery mode does not work. Same error message.

Also, I removed the profile option after using it once; I don't believe this is the problem. It was immediately after installing Bootchart that my computer wouldn't boot.

I'm able to boot up to a Live CD. Is there some way to fix it through there? Reformatting is not an option for me.

---

