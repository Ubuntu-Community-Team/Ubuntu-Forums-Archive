---
title: "changing login screen color in HH 8.04"
date: 2008-06-04
forum: General Help
---

### Post by alwiap on 2008-06-04
Hi,

I'm running ubuntu hardy heron 8.04, and I used to use this thread [http://ubuntuforums.org/showthread.php?t=565293&highlight=change+login+colour]("http://ubuntuforums.org/showthread.php?t=565293&highlight=change+login+colour") to change the color of the login screen (default it's a orangish screen) to a color I wanted, but I have made that change in 8.04 listed in the thread and it didn't change anything.  Anyone know how to change it in 8.04?

---

### Post by Forlong on 2008-06-04
Run ```
sudo gdmsetup
```
and go to the **Local** tab, there you'll find an option for the **Background color**.

---

### Post by alwiap on 2008-06-04
> **Forlong said:**
> Run ```
sudo gdmsetup
```
and go to the **Local** tab, there you'll find an option for the **Background color**.

Every time I do that, it opens gdmsetup for about 1 second, and then closes and terminal output says 'Segmentation fault'.

:confused:

Thanks for the info though!

---

### Post by Forlong on 2008-06-04
Well, it works here, so it's hard to debug this from here with such limited info.
You might want to start a bugreport over at launchpad for that.

---

