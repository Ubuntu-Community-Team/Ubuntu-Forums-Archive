---
title: "Recursive File Permissions in Nautilus not working, can't own Firefox Profile. [Resol"
date: 2007-04-22
forum: General Help
---

### Post by Bastanteroma on 2007-04-22
I'm trying to change the ownership and permissions of a bunch of folders using Nautilus as root, but the changes I make aren't being applied, even though I click the "apply permissions to enclosed files" button.

Instead of being writable and creatable by all users , the files inside are now owned exclusively by user id "500".

Should I just find instructions on using the command line?

---

### Post by taurus on 2007-04-22
```
gksudo nautilus
```

---

### Post by aysiu on 2007-04-22
Command-line probably won't fail. ```
sudo chown -R username:username /path/to/folder
```

I'm assuming there are folders within your /home/username directory that, for some strange reason, don't belong to username.

Do **not** change ownership of system folders to user. This can really screw up your system.

---

### Post by Bastanteroma on 2007-04-22
That did the trick - thanks aysiu.

---

