---
title: "Using WINE to run Windows programs stored on an NTFS partition?"
date: 2006-12-27
forum: General Help
---

### Post by i.wanna.corndog on 2006-12-27
Hey everybody,

I've been using Ubuntu for about the past month and am LOVING the experience. I have only booted into Windows about 3 times to grab some files and now that I have NTFS-3G working I think it may be a more permanent switch.

Anyway, I am trying to figure out if there is any way to configure WINE to run programs off of my mounted NTFS drive with full support. I haven't been using WINE for too long, but it seems that it simply creates a C-drive folder on the EXT3 partition and stores all the registry settings there. I know this may be a long shot, but could I configure WINE to read its "registry" from the NTFS partition and have its Windows folder read from the NTFS partition. Theoretically, this would allow me to run installed Windows programs without having to also install them on the EXT3 partition, so I can save space.

Is this all savvy, or am I not making any sense here...? I'm sure someone else has asked the question elsewhere, but I have searched and alas, I am stuck.

I'd greatly appreciate any help I can get here.

Thanks,
Dan

---

### Post by meng on 2006-12-27
Have you tried
winecfg
?

---

### Post by i.wanna.corndog on 2006-12-27
This takes care of the whole set drive C to the correct location problem, but what about the registry issues? I can set drive C to be at /mount/Windows, but there's no place (that I see) to point WINE to for registry settings (which IIRC, are stored in /Windows/system32/config). I could probably copy those settings over to WINE, but I don't want to have to update WINE's registry every time I install a new program from Windows.

Thanks,
Dan

---

### Post by hikaricore on 2006-12-27
I don't believe that you'll be sucessful in trying to use the windows registry for running software in wine, if what it seems like you are trying to do is actually what you are trying to do.  You will need to install or atleast configure most applications that require registry entries in linux no matter what.  Someone correct me if I'm wrong but I don't quite think it's going to work the way you expect it to.

---

