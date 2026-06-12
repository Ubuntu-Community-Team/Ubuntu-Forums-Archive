---
title: "Adept Manager Doesn't Ask For Password"
date: 2007-10-27
forum: General Help
---

### Post by myoungf1 on 2007-10-27
First off sorry if there is a thread open on this already and if there is can you point me to it.  When I go to open Adept Manager, in Gutsy it fails to bring up the password window and goes directly to Adept Manager.  I can go in and manage repositories and update and install programs.  In Feisty it always asked for a password before opening the Adept Manager but now it doesn't. 

My question is, is this a bug or was this done purposefully?

Thanks for anyones help.

---

### Post by taurus on 2007-10-27
Did you use sudo or any root privilege apps within the 15 minutes when you ran adept?

---

### Post by FuturePilot on 2007-10-27
I think this is a new feature which is part of the new kdesudo. In Gnome gksudo would remember your password for 15 minutes. In Gutsy they've replaced kdesu with kdesudo and I think it works much like gksudo in that it remembers your password for 15 minutes.

---

### Post by myoungf1 on 2007-10-27
Thanks for the info.  I decided to wait before opening Adept Manager again and voila it pulled up the Password window.  Good to know that there is a 15 minute remembering of the sudo password.

---

