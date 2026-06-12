---
title: "Sessions startup not working"
date: 2007-05-07
forum: General Help
---

### Post by dignick on 2007-05-07
I'm trying to add applications to the startup applications in system/preferences/sessions/startup programs.  If I add an application, close sessions and go back, the list is reverted back to how it was before and the application does not load when I login.

Any ideas?

Thanks.

EDIT: I'm using feisty.

---

### Post by Dfects on 2007-05-07
I have exactly the same problem :( Anyone?

---

### Post by dignick on 2007-05-07
bump

---

### Post by dignick on 2007-05-08
Please, anyone?  I'm  guessing as it isn't just me with this problem its a bug, and likely a feisty bug.  Can someone at least test it to see if it works for them?

Thank you.

---

### Post by sthapit on 2007-05-08
i have the same issue as well.

---

### Post by dignick on 2007-05-10
I hate doing it, but I'm bumping this message again.
I have seen that using sudo to launch sessions may fix it, but won't this add the startup item for all users?

---

### Post by Dfects on 2007-05-11
Bump ?! :(

---

### Post by orb9220 on 2007-05-11
Ok shooting in the dark here.

Open session's
check Sessions Options Is Automatically save changes checked?
and
Open users and accounts.
right click your user account does it look like mine?

Especially the administer accounts setting

Just checking things.
May not help.

---

### Post by aidanr on 2007-05-11
try: 
```
sudo chown -R username ~/.config
sudo chgrp -R username ~/.config
sudo chmod -R 755 ~/.config
```
replace username with your username

---

### Post by dignick on 2007-05-12
> **aidanr said:**
> try: 
```
sudo chown -R username ~/.config
sudo chgrp -R username ~/.config
sudo chmod -R 755 ~/.config
```
replace username with your username

Worked!  Thanks a lot.

Now why weren't permissions set correctly by default?

---

### Post by Dfects on 2007-05-15
> **aidanr said:**
> try: 
```
sudo chown -R username ~/.config
sudo chgrp -R username ~/.config
sudo chmod -R 755 ~/.config
```
replace username with your username

Yup that appears to of done it! I'm working from a pretty much base install, so no idea how these perms got screwed up. Oh well :)

Thanks!

---

### Post by thikrat on 2007-07-12
This worked for me as well, but we still do not have an answer, why did this happen in the first place?  I don't consider myself a noob and this doesn't make any sense?  Only thing i can think of is that when installing an app, it overwrite something in the sessions and changed the privs by accident or because of sloppy programming.

---

