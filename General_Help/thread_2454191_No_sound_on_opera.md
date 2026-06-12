---
title: "No sound on opera"
date: 2020-11-24
forum: General Help
---

### Post by hervera on 2020-11-24
Hi,

I just installed Opera on my ubuntu, but I don't have the sound on it. Does someone has a solution ?

---

### Post by Frogs Hair on 2020-11-24
Hello and Welcome hervera.

You might try installing the following package/s. Copy and paste the command in the terminal and enter your password. Restart the browser afterwards. Opera does have issues with certain video formats on Linux, but I don't know of any audio problems. 

```
sudo apt install ubuntu-restricted-extras  
```

---

### Post by deadflowr on 2020-11-24
How'd you install opera?
It can be installed either through the Ubuntu software store, which is a snap version.
Or downloaded and installed from opera, (I think it still has a deb version)

If from the software store, open the store and navigate the installed section and click to open opera's page.
Up in the top it should show 3 tabs, launch, remove, permissions.
Check the permissions to see if *play and record sound* is enabled.

---

### Post by hervera on 2020-11-25
Thank you it works now !

---

### Post by hervera on 2020-11-25
I have both, it didn't worked just on the version installed through the Ubuntu software store.

---

