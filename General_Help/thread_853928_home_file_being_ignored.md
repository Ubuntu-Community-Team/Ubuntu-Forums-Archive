---
title: "home file being ignored?"
date: 2008-07-09
forum: General Help
---

### Post by kneewax on 2008-07-09
Logged on to Ubuntu this morning and after entering my password the following error popped up:

"User's $home/.drmc file is being ignored. This prevents the default session from being saved. File should be owned by the user and have 644 permission.  User's $home directory must be owned by user and not writeable by other users"

Once logged in Ubuntu seems to be working OK, but I am concerned about the implications of the error.

Anyone got any ideas?

---

### Post by nikgare on 2008-07-10
I had this last week and this is how I fixed it:
I deleted the file .dmrc in my home directory, then I ran **touch .dmrc** ina a terminal.

---

### Post by kneewax on 2008-07-10
Thanks.  I fixed it using the following suggested elsewhere:

```

sudo chmod 644 /home/username/.dmrc
sudo chown username: /home/username/.dmrc
sudo chmod 755 /home/username
sudo chown username: /home/username
sudo shutdown -r now

```

Not sure if one method better, but this one worked for me.

Ta

---

### Post by roger_1960 on 2008-10-08
Hi

Thanks kneewax, this worked for me too.

---

