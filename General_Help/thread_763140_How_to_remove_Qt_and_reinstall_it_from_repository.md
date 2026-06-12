---
title: "How to remove Qt and reinstall it from repository?"
date: 2008-04-22
forum: General Help
---

### Post by MountainX on 2008-04-22
I installed Qt4 using the instructions I found at the TrollTech site:
[ftp://ftp.trolltech.com/qt/source/INSTALL](ftp://ftp.trolltech.com/qt/source/INSTALL)

Now I see that I could install Qt4 from the Ubuntu repositories. How do I clean my system up (i.e., remove the installation of Qt4 I did manually)?

My requirements are:
    *  Qt Version 4.1 or higher
    * Python Version 2.3 or higher
    * PyQt Version 4.0 or higher
    * An XML parser, such as python-xml
    * aspell

I have all this installed. Python is already installed by default, of course. First I installed Qt/X11 Open Source Edition 4.3.4. Then I installed the rest from synaptic. So that's where I am. I'd like to get back to the repository version of Qt4, but I also don't want to have to reinstall all my other stuff if I can help it. 

Thanks

---

### Post by MountainX on 2008-04-25
bump

---

### Post by natrixgli on 2008-04-25
If you still have the original install files, check the README and INSTALL files, usually you can do something along the lines of 'sudo make remove' and/or 'sudo make uninstall' etc... 

Cheers,

-n8

---

