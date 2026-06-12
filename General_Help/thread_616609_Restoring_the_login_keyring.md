---
title: "Restoring the login keyring"
date: 2007-11-18
forum: General Help
---

### Post by zumbrujm on 2007-11-18
Yesterday I was reading a how-to, and instead of deleting the default keyring, which I was supposed to do, I deleted the login keyring.  When I rebooted, the GUI gives me a popup saying authentication failed, before I can type anything into the login window.  When I switch back to the terminal, I can log in  still.  I'm running the latest version of Ubuntu, and was wondering if there is any way to restore or remake that keyring.

Thanks for your help.
John Z.

---

### Post by Giro on 2007-12-20
I am having the same problem. I have the login.keyring file in my recycle bin, but I do not know how to access it from the recovery mode. Any help on this topic would be greatly appreciated.

---

### Post by Giro on 2007-12-20
I got mine working again. Turns out, deleting the keyring is fine. It doesn't ask me for a keyring password anymore, which is what I wanted. I was following another solution to remove the keyring and it had me write me a line of code into the gdm file, and when I removed the line it let me login again.

---

### Post by Almumin on 2008-01-07
You can find the trash located under /home/username/.Trash

---

