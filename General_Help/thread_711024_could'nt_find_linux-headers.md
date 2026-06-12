---
title: "could'nt find linux-headers"
date: 2008-02-29
forum: General Help
---

### Post by Riadh-Temala on 2008-02-29
Hello guys,

I'm tryin those days to setup my wireless network card (vt6656 from viarena) in ubuntu linux, but i'm facing some problems:

when i follow the tutorial gived by the manufacturer, i encounter always the same error:

# sudo apt-get linux-headers-$(uname -r)

E: Could'nt find packages linux-headers-2.6.16.29-xen

where can i find those packages?

thanks for any support.

---

### Post by PeterJS on 2008-02-29
You could use the linux-headers-xen metapackage. What version are you running that's using a kernel that old? Xen is a virtualized environment, shouldn't the host OS be handling the hardware?

---

