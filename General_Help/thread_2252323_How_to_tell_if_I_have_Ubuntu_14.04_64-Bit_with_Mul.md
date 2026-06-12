---
title: "How to tell if I have Ubuntu 14.04 64-Bit with Multiarch or without Multiarch?"
date: 2014-11-11
forum: General Help
---

### Post by carmen2012 on 2014-11-11
I'd like to use Team Viewer for Ubuntu and on the Team Viewer download page ([http://www.teamviewer.com/en/download/linux.aspx](http://www.teamviewer.com/en/download/linux.aspx)), there are two options for Ubuntu.  One is with Multiarch and the other is without.

How do I tell which one to download.  I did go through their website but really wasn't clear on this.  I am using Ubuntu 14.04 LTS.

Thank you

Carmen

---

### Post by plucky on 2014-11-11
> **carmen2012 said:**
> I'd like to use Team Viewer for Ubuntu and on the Team Viewer download page ([http://www.teamviewer.com/en/download/linux.aspx](http://www.teamviewer.com/en/download/linux.aspx)), there are two options for Ubuntu.  One is with Multiarch and the other is without.

How do I tell which one to download.  I did go through their website but really wasn't clear on this.  I am using Ubuntu 14.04 LTS.

Thank you

Carmen

what does ```
dpkg --print-architecture
``` 

and also ```
dpkg --print-foreign-architectures
```

show you?

---

### Post by grahammechanical on 2014-11-11
Ubuntu 14.04 64 bit comes with multiarch libraries by default as the process started with Ubuntu 11.04 with the change over coming in Ubuntu 12.04.

[https://help.ubuntu.com/community/MultiArch](https://help.ubuntu.com/community/MultiArch)

[https://wiki.ubuntu.com/MultiarchSpec](https://wiki.ubuntu.com/MultiarchSpec)

Regards.

---

