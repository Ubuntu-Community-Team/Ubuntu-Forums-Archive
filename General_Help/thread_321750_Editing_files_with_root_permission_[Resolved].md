---
title: "Editing files with root permission [Resolved]"
date: 2006-12-19
forum: General Help
---

### Post by diw on 2006-12-19
I've been trying to edit /usr/lib/realplay-10.08/realplay to change a setting as I'm having a problem with stuttering video/audio on the bbc website.

I have been trying to use sudo gedit but as the file is also an executable this only serves to execute the file whereas I want to edit one of the lines.  How do I do this please - I'm using Edgy but am used to using another distro where working in root is quite simple.

---

### Post by kd7swh on 2006-12-19
you could try a different editor.

I use emacs for most of my stuff.

if you need to install it you can use:

"sudo apt-get install emacs"

just run emacs or nano as root an see if that does the trick.

---

### Post by aysiu on 2006-12-19
Try ```
gksudo nautilus
``` More details here:
[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by holdinout on 2006-12-19
Aaysiu, are you hunting people with file sharing problems? :-D

---

### Post by diw on 2006-12-19
Thanks master roaster - worked a treat!

---

