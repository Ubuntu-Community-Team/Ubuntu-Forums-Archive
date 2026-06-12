---
title: "how do I access a shared folder on another pc ?"
date: 2007-11-12
forum: General Help
---

### Post by madjack on 2007-11-12
how do I access a shared folder on another pc ?

---

### Post by whitewizardcoder on 2007-11-12
Is the other pc running Windows?  If so, you can open the share by opening nautilus, clicking on the button that looks like a paper and pencil (this will let you manually enter a location), and inputting "smb://<computer_name>" replacing <computer_name> with the name of your other pc, or if that doesn't work "smb://<computer_ip>" where <computer_ip> is the IP address of your other pc.  You should now be able to access the shares on that computer.

Hope this helps!

---

