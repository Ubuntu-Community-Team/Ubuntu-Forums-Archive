---
title: "[SOLVED] security question"
date: 2007-06-12
forum: General Help
---

### Post by scragar on 2007-06-12
I just installed Lampp, and since I've had Xampp the windows version before I knew what to expect however after following it's instilation instructions I found that the standard text editor would not allow me to edit any files within the /opt folder.

Is there any way to give it temparary pemitions to do such a thing or simply reduce the required permitions? or will I have to install it to a moreacceptable directory which I can edit?

---

### Post by taurus on 2007-06-12
```
sudo nano -Bw filename
```
Save and exit with <Ctrl>o and <Ctrl>x.

---

