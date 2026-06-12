---
title: "Executable to execute command line"
date: 2008-06-14
forum: General Help
---

### Post by codeking on 2008-06-14
I need to make an executable to execute the following line from the command line:

```
sudo /opt/lampp/lampp start
```

How would I go about doing this?  I'm proficient in C, so any programming I would need to do would be fine.

---

### Post by amingv on 2008-06-14
No C programming needed at all, just make a file with these lines:

[PHP]#!/bin/bash

sudo /opt/lampp/lampp start
sudo -k[/PHP]

save it as whatever you like (preferably with .sh extension) and run this command:
```
chmod a+x <myfilename>.sh
```
and run it as
```
./<myfilename>.sh
```

As another option, you could make an alias:

```
alias <functionname>="sudo /opt/lampp/lampp start"
```
and run it as
```
<functionname>
```

You'd need to copy that line at the bottom of ~/.bashrc to make it permanent.

---

### Post by ChameleonDave on 2008-06-14
> **codeking said:**
> I need to make an executable to execute the following line from the command line:

```
sudo /opt/lampp/lampp start
```


It depends on how you want to call this new executable.  The entering of the password needs to be handled.

If you want something you can click on, try putting this in the file instead of a bash script:
```

[Desktop Entry]
Comment=This will run the command /opt/lampp/lampp start as root.
Exec=echo "Trying to start lampp..." && sudo /opt/lampp/lampp start && sleep 3s
GenericName=lampp start
Icon=terminal
MimeType=
Name=lampp
StartupNotify=true
Terminal=true
#TerminalOptions=\s--noclose
Type=Application

```

Save it as *~/Desktop/Start_lampp.desktop*.

---

