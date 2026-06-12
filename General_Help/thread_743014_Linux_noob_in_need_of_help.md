---
title: "Linux noob in need of help"
date: 2008-04-02
forum: General Help
---

### Post by Slow VR on 2008-04-02
I get an authentication error on startup and am unable to login with the standard splash screen.

Here's the link to a thread I found. I have the exact same problem.
[http://ubuntuforums.org/showthread.php?t=687236]("http://ubuntuforums.org/showthread.php?t=687236")

This is what he said worked, I just don't know the steps I need to take to fix it. I tried doin ctrl+alt+F2 and I was able to login so I'm assuming everything else is fine, I just need a step by step guide on how to fix this.

SOLVED: I had to delete the include common-pamkeyring from gedit /etc/pam.d/gdm

To get into the file without using Gedit, I used sudo nano and then the pathname

Any help would be greatly appreciated!

---

