---
title: "f-spot 0.3.0 and Drapper Drake"
date: 2006-12-17
forum: General Help
---

### Post by Matt Z on 2006-12-17
Hello!
Has any one installed f-spot 0.3.0 on Ubuntu 6.06 LTS? I can't find any deb package for this distribution.
While I try to install it from sources i have the following error:

```
No package 'libgnome-2.0' found
No package 'libgnomeui-2.0' found
No package 'gtk+-2.0' found
```

libgnome-2.0 is installed, but i can't find gtk+-2.0 in the repository.

Can anyone help me with this instalation?

---

### Post by hanzomon4 on 2006-12-17
You need the dev packages 
[LIST]
[*]libgnome2.0-dev
[*]libgtk2.0-dev
[*]libgnomeui-dev
[/LIST]

This should get you going > sudo apt-get install automake1.9 build-essential intltool libtool cvs
sudo apt-get build-dep f-spot


---

### Post by Matt Z on 2006-12-17
> **hanzomon4 said:**
> You need the dev packages 
[LIST]
[*]libgnome2.0-dev
[*]libgtk2.0-dev
[*]libgnomeui-dev
[/LIST]

This should get you going

it works. Thank you.

---

### Post by QwUo173Hy on 2006-12-18
I have been warned in the past that you shd never install source packages on a system that uses a package manager in case the package manager gets confused.

I am surprised that there isn't a package available for this since it seems to be a core Gnome app and that the latest version has been out for three weeks.

---

### Post by srf21c on 2007-03-30
I always use the checkinstall utility to install programs that I build from source.  This creates a package from the newly built program which can then manipulated like any other debian package. 

So instead of typing "sudo make install" as the final build step, try "sudo checkinstall" instead.

---

