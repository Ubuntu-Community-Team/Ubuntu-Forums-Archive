---
title: "wine issues -- network related?"
date: 2007-06-03
forum: General Help
---

### Post by bmeyer on 2007-06-03
I'm trying to install Photoshop 7.0 with wine.  When it gets to 8% installed, I receive the following:
```

ComponentMoveData had the following error:

Media Name: data
Component: App_Photoshop\Web
File Group: Web
File: c:\Program Files\Common Files\Adobe\Web\AdobeBannerenu.awe
Error Number: -115

```

Has anyone ever seen anything like this?  Is it network related; is wine trying to download files and failing?  It's a desktop with PCI wireless.  NetworkManager is removed and network is started with ifup and the network interface file.

And no, I won't use GIMP instead ;)  Thanks in advance for the help!

---

### Post by bmeyer on 2007-06-05
Any ideas?

---

### Post by bmeyer on 2007-06-12
Lol, this is still an issue.  if anyone has ever run across this and have any ideas, I sure would appreciate it :)

---

### Post by m234 on 2007-11-25
Had the some problem... In my case the 'Adobe' folder as shown in the file path in your error message had strangely only root permissions. After changing these permissions to my user's the hole installation process just worked fine...

---

