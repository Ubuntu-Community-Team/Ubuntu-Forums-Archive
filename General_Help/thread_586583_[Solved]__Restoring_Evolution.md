---
title: "[Solved]  Restoring Evolution"
date: 2007-10-22
forum: General Help
---

### Post by PartisanEntity on 2007-10-22
I backed up my home folder before installing Gutsy, now I would like to restore my Evolution files and settings. I copied .evolution from the backup location to my new /home folder. However when I started Evolution the Wizard starts up to help me set up an account.

What other files need to be copied and to where in order for Evolution to start with all my previous settings, emails and accounts?

I looked through some threads here but nothing seemed tried and tested with feedback.

Thanks.

---

### Post by ruibernardo on 2007-10-22
Hi,

I did not tried this with Gutsy, but this [link]("http://ubuntu.wordpress.com/2005/12/03/how-to-backup-evolution/") has been working for me since Dapper. It says that the Evolution directories are:

```
~/.evolution/
~/.gconf/apps/evolution/
~/.gnome2_private/Evolution
```

---

### Post by PartisanEntity on 2007-10-22
Okay I copied those over, but when starting Evolution, I am still only greeted by the set-up Wizard.

---

### Post by PartisanEntity on 2007-10-23
Update:

It worked. Here is what I did:

1. First, you launch Evolution, go through the set up Wizard and set up an email account.
2. Then you shut down Evolution, and copy the files mentioned above by **epimeteo**.
3. Then you restart Ubuntu

You should then have all your emails and contacts restored.

The only thing you will need to do is add your email addresses manually.

If anyone has a better or easier method, please post it.

---

