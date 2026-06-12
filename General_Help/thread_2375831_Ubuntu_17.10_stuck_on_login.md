---
title: "Ubuntu 17.10 stuck on login"
date: 2017-10-27
forum: General Help
---

### Post by ulysses77 on 2017-10-27
I just finished setting up my new installation too! I don't want to have to reinstall, no idea why it's not working. The laptop is an AMD HP laptop. 

Running as Xorg will get the wallpaper to appear before going back to the login screen, as normal, no wallpaper at all, blank until returning to the login screen.

---

### Post by monkeybrain20122 on 2017-10-27
Sounds like what happened to me though I can log into xorg. [https://ubuntuforums.org/showthread.php?t=2375743](https://ubuntuforums.org/showthread.php?t=2375743)

---

### Post by ulysses77 on 2017-10-27
What happened?

Any solutions?

Ok, a temporary solution until they patch this crap.  

rm -rf /home/ulysses/.config/dconf/user

This will get you in, this will give you stock every time, but your files will be there. Can somebody submit this issue to the higher ups?

---

### Post by monkeybrain20122 on 2017-10-28
> **ulysses77 said:**
> Ok, a temporary solution until they patch this crap.  

rm -rf /home/ulysses/.config/dconf/user

This will get you in, this will give you stock every time, but your files will be there. Can somebody submit this issue to the higher ups?
 Well I can get in to xorg, but not wayland. I am not sure what caused it though I suspect it might be an update. I will try a clean install again and see... Fortunately this is a test install and don't mind nuking it.

---

### Post by ulysses77 on 2017-10-28
That's good, let me know what you find

---

### Post by monkeybrain20122 on 2017-10-29
Did a reinstall and update now everything works. Strange.

---

### Post by ulysses77 on 2017-10-29
Really? Well as long as it all works. Strange though.

---

### Post by monkeybrain20122 on 2017-10-30
I found the answer to my issue. The culprit is the Easyscreencast extension. Enable it, no Wayland, disable it can login to Wayland again. Unfortunately I don't think this is the same problem you reported.

---

