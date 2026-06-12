---
title: "[SOLVED] .Deb Illiterate"
date: 2007-02-12
forum: General Help
---

### Post by Zeotronic on 2007-02-12
Whenever I try to open a .deb file, before it finishes loading I get an error message that looks roughly like this:
> [B]Could not open
'inkscape_0.44-1ubuntu2_i386.deb'[/B]

The package might be corrupted or you are not allowed to
open the file. Check the permissions of the file.

That just being word for word the last one I've gotten. I have reason to suspect that these .debs are in-fact not corrupt, because it happens whenever I try to open any .deb I've got on my system. However, my permissions should be fine, because I'm using the only account on this computer besides root.

---

### Post by Maestro23 on 2007-02-12
Couple of links for you to read/bookmark. Might help.

Installation of Software:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

**For Frijolie's suggestion, you might have to enable extra repositories: [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Frijolie on 2007-02-12
why not just 

```
sudo apt-get install inkscape
```

?

---

### Post by Zeotronic on 2007-02-12
I cant just do that nice bit of code you just threw out because it doesn't work for me... But I'm running Xubuntu from my install disk right now and all of the problems that I have been having are totally gone so I'm just going to reinstall Xubuntu. Problem solved (god I hope so anyways).

---

### Post by majoridiot on 2007-02-13
have you tried (from the directory the .deb resides in:

```
sudo dpkg -i inkscape_0.44-1ubuntu2_i386.deb
```

---

