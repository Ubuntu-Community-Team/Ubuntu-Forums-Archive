---
title: "Lost &quot;X&quot;"
date: 2005-10-15
forum: General Help
---

### Post by fiby on 2005-10-15
I tried installing xfree86 4.5.0 and now The desktop doesn't load.  All I get is a terminal like screen.   How can I restore desktop?

---

### Post by DJ_Max on 2005-10-15
Why were you installing Xfree86 when Breezy uses Xorg? How did you install it?

---

### Post by az on 2005-10-15
If you changed your sources.list, change it back.

then run
sudo apt-get update
sudo apt-get install x-window-system-core

and then 
sudo apt-get -f install

and let me know how that works out for you...

---

### Post by fiby on 2005-10-15
I used the binaries from xfree86

---

### Post by fiby on 2005-10-15
no working for me, here is  error  msg: "failed to start x-server" "x-server  disabled restart gdm"

---

### Post by fiby on 2005-10-15
I get this error,  /usr/x11r6/bin/x 0 -br -audit0 -auth/var/lib/gdm :0.Xauth -nolisten tcp vt7, no path

wants me to install "x server" and restart gdm

---

