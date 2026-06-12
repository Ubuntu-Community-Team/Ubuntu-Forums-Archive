---
title: "Transfering home directory to a new installation"
date: 2007-02-05
forum: General Help
---

### Post by prion on 2007-02-05
I recently reinstalled Kubuntu 6.06 onto my computer and replaced the /home/<username> directory with a saved copy of my last installation's /home/<username> directory to maintain files/settings/etc.  When I log in to the KDE terminal I get the error message:

"There was an error message setting up interprocess communications for KDE.  The message returned by the system was: Could not open network socket.  Please check that the "dcopserver" program is running!"

I thought it might be a permissions problem originally, but resetting the permissions hasn't helped.  If anyone has seen this problem before I'd love some advice.  Thanks!

---

### Post by llamakc on 2007-02-05
What about ownership?

cd ~

sudo chown -R YOURNEWUSERNAME:YOURNEWUSERNAME .

Don't forget that "." at the end either.

---

### Post by bettlebrox on 2007-02-05
Yeah, check the ownership of all you files. Plus, look in the .kde directory and remove the files that start with:
cache-*  
socket-*  
tmp

---

### Post by prion on 2007-02-06
Thanks for the help

- prion

---

### Post by bettlebrox on 2007-02-06
What sollved the problem?

---

### Post by prion on 2007-02-07
I did both: deleted the files and then changed the ownership.

---

