---
title: "Save installed apps and re-installation"
date: 2008-06-17
forum: General Help
---

### Post by ocasasola on 2008-06-17
Hello, is there any option to save the list on the synaptic package manager of installed apps? I mean, I have configure that all installed apps once are installed, are removed from the hard drive, installed and deleted in other words.

If by any reason, I have to reinstall the OS as ubuntu 8.04 (clean install and from scratch), can I get the list on installed apps and attached to the synaptic package manager for download automatic my current status of installed apps?

Also, I have add the aptoncd, but keep the original config about installed aps as above describe (download, install and delete).

Thank you for any further assistance. Best regards,

---

### Post by editrix on 2008-06-17
Not sure if this is what you mean, but in /var/cache/apt/archives is all the .deb packages you've installed. They won't stay there forever, unless something's changed since Dapper.

Anyway, what you can do is copy them to CD--or, so as not to waste CD space, save them anyplace, then when there's enough to fill a CD copy them to CD. Then you just have to add that CD as a repository.

You'll have to be root to do anything with /var/cache/apt/archives.

---

### Post by geirha on 2008-06-17
You might have luck with this guide [http://www.ubuntugeek.com/clone-your-ubuntu-installation.html](http://www.ubuntugeek.com/clone-your-ubuntu-installation.html)

---

### Post by ocasasola on 2008-06-18
Thank you very much, helps me a lot! I would work on this...

Best regards :)

---

