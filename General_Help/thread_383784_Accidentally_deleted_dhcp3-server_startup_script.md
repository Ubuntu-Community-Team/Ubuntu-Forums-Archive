---
title: "Accidentally deleted dhcp3-server startup script"
date: 2007-03-13
forum: General Help
---

### Post by timer on 2007-03-13
I happened to make a stupid mistake and deleted the following file on my Feisty installation :( . I can't seem to find anywhere to get this file back so I was wondering if anyone could just paste the default contents of this file so I can recreate it? 

Any help much appreciated,
Timer

---

### Post by peabody on 2007-03-13
Do you know the full path of the file?  If so, I think the "dpkg -S /path/to/file" command will tell you the package it was part of (even if the file's not on your drive anymore.  It would probably just take a re-installation of the .deb to restore it.  Download the package it tells you and do a "dpkg -i filename".

---

### Post by timer on 2007-03-14
Thanks, for the info, it worked like a charm once I learned about how to use dpkg. Finally got the file back once I purged the Dhcp3-server package from the system and then forced an installation of it. 

Thanks you very much for the help
Timer

---

### Post by peabody on 2007-03-14
> **timer said:**
> 
Thanks you very much for the help
Timer

You're totally welcome!  I'm glad my advice worked out.

---

