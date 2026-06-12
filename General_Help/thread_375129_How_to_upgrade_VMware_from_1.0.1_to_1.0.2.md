---
title: "How to upgrade VMware from 1.0.1 to 1.0.2"
date: 2007-03-03
forum: General Help
---

### Post by rainwalker on 2007-03-03
I just opened VMware (server console) and it said that there is a new version available at the VMware site, so I went there and I'm on the downloads page right now. My question is, by the looks of the downloads page, I have to totally re-install VMware to upgrade? I'm used to the way Firefox upgrades/updates, where it basically does it all for you (I know, I'm lazy), so I'm unsure as to how I should go about upgrading VMware. Any tips?

---

### Post by rainwalker on 2007-03-03
Is it possible to use apt-get to do this?

---

### Post by jocko on 2007-03-03
No need to uninstall the older version. Just get the new file from vmware's  website and follow the same instructions you used to set it up originally. The installer will detect the old version and replace it.

---

### Post by rainwalker on 2007-03-03
Um...could you tell me how to install it? I've totally forgotten how I did it the first time.

---

### Post by rainwalker on 2007-03-03
All I've done is saved the VMware-server-1.0.2-39867.tar.gz file to my desktop, but I can't remember where to go from there.

---

### Post by zeus77 on 2007-03-03
Right-click, select "extract here" to unzip/tar the archive to the desktop.  then from the command line, run the install script vmware-install.pl (make sure to use sudo).

---

### Post by rainwalker on 2007-03-03
What is the directory that contains the init directories (rc0.d/ to rc6.d/)?

---

### Post by jocko on 2007-03-03
> **rainwalker said:**
> What is the directory that contains the init directories (rc0.d/ to rc6.d/)?
Just hit enter to accept the default answers to all questions about directories. They are all correct.

---

### Post by rainwalker on 2007-03-04
Thanks for all the help, but I've decided to uninstall VMware because I really never use it.
Do you know how to uninstall it?

---

### Post by scxtt on 2007-03-04
you should have a "vmware-uninstall.pl" script - run that ...

---

### Post by rainwalker on 2007-03-04
I did that, and the terminal opens and then immediately closes. What's happening?

---

### Post by scxtt on 2007-03-04
hard to say, especially if you'd done anything non-"vmware-uninstall.pl" related ... what is the exact command you are running from the terminal?

---

### Post by rainwalker on 2007-03-05
I'm not running it from the terminal; I went to the location of the script in the File Browser, double-clicked the script, and chose "Run In Terminal"

---

### Post by scxtt on 2007-03-05
eh, that's not gonna work well ...

open a terminal window and type:

sudo /path/to/vmware-uninstall.pl
(replace "/path/to" w/ the full location to the script [/usr/lib/vmware maybe])

---

### Post by rainwalker on 2007-03-05
Oh okay, I hadn't tried accessing as well as running it from the terminal. I'll try that when I get home.

---

