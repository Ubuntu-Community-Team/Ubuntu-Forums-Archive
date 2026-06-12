---
title: "What is the terminal command for delete?"
date: 2007-04-08
forum: General Help
---

### Post by Espreon on 2007-04-08
I need 2 know so I can delete a folder that belongs to the root account, since I accidentally installed Wine-Doors as root, I can't get a clean reinstall without deleting the folder it made and the config files in the .wine folder.

---

### Post by aysiu on 2007-04-08
Actually, you don't.

1. [You don't need the terminal to delete folders that belong to the root account.](http://www.psychocats.net/ubuntu/permissions)

2. The /home/espreon/.wine folder should already belong to your account, so you should be able to just delete any subfolder in there.

3. But, just in case you do want the terminal command, it's ```
sudo rm -r *nameoffolder*
``` **Warning**: The phrase *sudo rm -r* should never be typed in the terminal. It can be very dangerous. If you accidentally hit the Enter key too soon, you might delete your entire installation and have no way to recover certain files.

---

### Post by Espreon on 2007-04-08
Thanx

---

