---
title: "Install systemwide"
date: 2007-04-22
forum: General Help
---

### Post by Martje_001 on 2007-04-22
Hi,
I've wrote a script (SABnzbd for Linux, based on jtt1560's work), but it doesn't work well on Feisty. I want to write the whole script again, and I want the script (the program) installed systemwide. Where can I install it? Which directory is available for all users?

Thank you!
Martin

---

### Post by mhansen on 2007-04-22
You can type:

echo $PATH

and it'll show you the path Linux uses to search for any executable run.  An executable in any of these directories is available system wide.  Just make sure you have the permissions set properly.

For what it's worth, I recommend /usr/local/bin as the installation directory for your script.  It's the "usual" place to install any binaries that aren't part of the distro itself, and keeps things nice and clean.



Regards,
Mike

---

