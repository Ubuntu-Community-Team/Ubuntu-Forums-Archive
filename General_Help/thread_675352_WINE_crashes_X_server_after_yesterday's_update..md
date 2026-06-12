---
title: "WINE crashes X server after yesterday's update."
date: 2008-01-22
forum: General Help
---

### Post by vexorian on 2008-01-22
I am not sure what I updated last night, I left the update manager doing its thing and I used the shutdown command so that it shuts down on 3:00 AM (the update was not supposed to take until much more than 1:00 AM ) 

When I turned my computer on today everything seemed fine. Until I attempted to open a windows executable with WINE, it looks like WINE would now make X server restart every time I try to use it.

It is not opengl related since I tested some opengl apps and they don't do this.

Any idea? How do I figure out what packages were installed last night?

---

### Post by rosegarden78 on 2008-01-22
Here's a link on restoring Xorg is that what you mean?
[http://ubuntuforums.org/showthread.php?t=675136](http://ubuntuforums.org/showthread.php?t=675136)

---

### Post by vexorian on 2008-01-22
It wasn't.

I didn't notice but one of the updates was X server.

I also thought I tested OpenGL but I didn't, looks like not every SDL app uses opengl automatically. Anyways, it looks like once again the nvidia driver has come to torment me, I had to reinstall it.

Never, never, install the driver from nvidia unless you card really doesn't work with the restricted drivers, even if it doesn't I don't think it is worth it...

---

### Post by heavyhenning on 2008-01-25
I can confirm this.
I can't start wine applications anymore after I updated a few days ago.. The X-server just plain crashes and GDM restarts.. As far as I can see, does not print error messages in the log..

:confused:

---

### Post by fyo on 2008-01-25
> **vexorian said:**
> It wasn't.Anyways, it looks like once again the nvidia driver has come to torment me, I had to reinstall it.

Never, never, install the driver from nvidia unless you card really doesn't work with the restricted drivers, even if it doesn't I don't think it is worth it...

I had the same problem. Turns out all that happens is that the xorg component drops in a new libglx.so thereby nuking the symlink of the same name pointing to the NVIDIA component.

Restoring the symlink is all that's required to "fix" things:

[http://ubuntuforums.org/showthread.php?t=671261](http://ubuntuforums.org/showthread.php?t=671261)

---

### Post by fyo on 2008-01-25
> **heavyhenning said:**
> I can confirm this.
I can't start wine applications anymore after I updated a few days ago.. The X-server just plain crashes and GDM restarts.. As far as I can see, does not print error messages in the log..

:confused:

This sounds like an issue that cropped up for a while a few days ago, but was since fixed... so upgrading to the very latest components should solve the problem:

[http://ubuntuforums.org/showthread.php?p=4159471](http://ubuntuforums.org/showthread.php?p=4159471)

Check your syslog, btw, it should have some error info...

```
$ tail /var/log/syslog
```

---

