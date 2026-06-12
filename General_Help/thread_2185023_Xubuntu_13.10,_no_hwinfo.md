---
title: "Xubuntu 13.10, no hwinfo"
date: 2013-10-31
forum: General Help
---

### Post by han2 on 2013-10-31
Hello,

It seems Xubuntu 13.10 doesn't come with *hwinfo* installed. When I try to install it I get this message:

```
Package hwinfo is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source

E: Package 'hwinfo' has no installation candidate
```

Is there any other way to get it?

Regards.

---

### Post by Toz on 2013-10-31
In a nutshell, hwinfo is dependent on hal, and hal has been deprecated in 13.10. For more informaiton, see [here]("https://answers.launchpad.net/ubuntu/+source/hwinfo/+question/237733"). There is a PPA listed there, but I can't comment on it since I haven't used it.

EDIT: The PPA is for hal, not hwinfo.

---

### Post by kurt18947 on 2013-10-31
> **han2 said:**
> Hello,

It seems Xubuntu 13.10 doesn't come with *hwinfo* installed. When I try to install it I get this message:

```
Package hwinfo is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source

E: Package 'hwinfo' has no installation candidate
```

Is there any other way to get it?

Regards.

I believe there's a package "hardinfo" in the repositories that displays a fair amount of system information.  Worth a try?

---

### Post by han2 on 2013-11-01
> **Toz said:**
> In a nutshell, hwinfo is dependent on hal, and hal has been deprecated in 13.10. For more informaiton, see [here]("https://answers.launchpad.net/ubuntu/+source/hwinfo/+question/237733").

Thanks, Toz. I see. Then I'd need to find an alternative to show supported resolution modes.

> **kurt18947 said:**
> I believe there's a package "hardinfo" in the repositories that displays a fair amount of system information. Worth a try?

Thanks, Kurt. It's a nice tool, but not what I'm looking for. 

There's an old script to fix the Plymouth screen after installing propietary drivers. [This script]("http://launchpadlibrarian.net/121675171/fixplymouth") uses hwinfo --framebuffer to show supported resolutions. I'd like to fix that line in the script to have it fully working in 13.10.
 
Is there any other command I could use to show supported resolutions?

Regards.

---

### Post by jpedromacedosilva on 2013-11-04
I have the exact same problem... If anyone knows a alternative for hwinfo or a diferent way to fix plymouth resolution in Ubuntu/Xubuntu, I'd be very thankful!

---

### Post by han2 on 2013-11-04
You don't need hwinfo to fix Plymouth; hwinfo only shows supported resolution modes. As an alternative to hwinfo you can use vbeinfo (pressing 'C' in Grub).

---

### Post by jpedromacedosilva on 2013-11-04
I've done that to! I used vbeinfo after pressing C in grub2.
I treid to use all resolutions listed in vbeinfo, but none of them woked for me.
I've tried fixing plymouth resolution using this turorial [http://randomandlinux.blogspot.pt/2013/05/fix-ubuntu-boot-screen-after-installing.html](http://randomandlinux.blogspot.pt/2013/05/fix-ubuntu-boot-screen-after-installing.html) and this one [http://randomandlinux.blogspot.pt/2013/06/fix-ubuntu-1304-boot-screen-plymouth.html](http://randomandlinux.blogspot.pt/2013/06/fix-ubuntu-1304-boot-screen-plymouth.html), and nothing worked for me.
This is still unsolved for me!

Best regards.

> **han2 said:**
> You don't need hwinfo to fix Plymouth; hwinfo only shows supported resolution modes. As an alternative to hwinfo you can use vbeinfo (pressing 'C' in Grub).

---

### Post by pqwoerituytrueiwoq on 2013-11-04
[http://packages.ubuntu.com/raring/hwinfo](http://packages.ubuntu.com/raring/hwinfo)
[http://packages.ubuntu.com/raring/libhd16](http://packages.ubuntu.com/raring/libhd16)
use the copy on 13.04, it still works on 13.10 (i have it from where i upgraded to 13.10)
save to file and install both using [FONT=courier new]sudo dpkg -i Downloads/{libhd16,hwinfo}.deb[/FONT]

---

### Post by never-never-land2 on 2013-12-04
> **jpedromacedosilva said:**
> I've done that to! I used vbeinfo after pressing C in grub2.
I treid to use all resolutions listed in vbeinfo, but none of them woked for me.
I've tried fixing plymouth resolution using this turorial [http://randomandlinux.blogspot.pt/2013/05/fix-ubuntu-boot-screen-after-installing.html](http://randomandlinux.blogspot.pt/2013/05/fix-ubuntu-boot-screen-after-installing.html) and this one [http://randomandlinux.blogspot.pt/2013/06/fix-ubuntu-1304-boot-screen-plymouth.html](http://randomandlinux.blogspot.pt/2013/06/fix-ubuntu-1304-boot-screen-plymouth.html), and nothing worked for me.
This is still unsolved for me!

Best regards.

perhaps you can try the solution given in here:
[http://iwillfolo.blogspot.com/2013/11/how-to-fix-your-elementary-os-plymouth.html](http://iwillfolo.blogspot.com/2013/11/how-to-fix-your-elementary-os-plymouth.html)
 
it might work for you better, it did for me... (method #1)

---

