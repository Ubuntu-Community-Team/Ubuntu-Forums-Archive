---
title: "Adding startup script to Xubuntu"
date: 2007-03-29
forum: General Help
---

### Post by richbiskit on 2007-03-29
How can i make xubuntu run this at start up?  sudo inputattatch --mouseman /dev/ttyS0

If i run it in a terminal i can use a 2nd mouse but when i shut the terminal it stops the mouse working. i need to make it work from startup!

---

### Post by paper0k on 2007-03-30
> **richbiskit said:**
> How can i make xubuntu run this at start up?  sudo inputattatch --mouseman /dev/ttyS0
Try to insert this command into /etc/rc.local before the "exit 0" command ;)

---

