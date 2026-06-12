---
title: "gnome panel stretched"
date: 2007-03-07
forum: General Help
---

### Post by tronica on 2007-03-07
I have dual monitors setup with twinview, and up intill now the gnome panel has stayed on one monitor, but now its stretched across both. how can i fix this. heres a screehshot

[http://itransfer.ath.cx/Screenshot.png]("http://itransfer.ath.cx/Screenshot.png")

Thanks

---

### Post by tribble222 on 2007-03-07
If you maximize a window does it stretch across both screens as well?

---

### Post by tronica on 2007-03-08
yeah

---

### Post by tribble222 on 2007-03-08
I think you probably have to add a xinerama option to your xorg.conf.  Something like xinerama on or off or NoTwinViewXineramaInfo.  Check out the possible flags here [http://us.download.nvidia.com/solaris/1.0-9746/README/appendix-d.html](http://us.download.nvidia.com/solaris/1.0-9746/README/appendix-d.html)

---

