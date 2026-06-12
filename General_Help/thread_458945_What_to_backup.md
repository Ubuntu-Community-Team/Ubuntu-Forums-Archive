---
title: "What to backup?"
date: 2007-05-30
forum: General Help
---

### Post by Bluecube on 2007-05-30
If I wanted to reinstall Ubuntu for one reason or another what directories should I backup to ensure that I can boot up my new install and have all my old settings only a file copy away? I know that the Home directory is important but what exactly does it contain? I think it has emails but what about the email settings for example? I've also read that the etc directory is important. Anything else?

---

### Post by pbw on 2007-05-30
Your home directory contains all of your user settings. To view them enter ls -a ~/ in terminal, or view hidden files in your file manager. /etc contains system settings and configuration. That's all i'd backup really, with exception to mysql databases and such. You could also backup your apt cache if you really wanted, to easily reinstall apps you had. *shrug*

If you're reinstalling, you should place /home on a seperate partition from root this time around. That way you can reinstall in the future or switch distros without worrying about losing important user files or settings.

-- pbw

---

### Post by floke on 2007-05-30
To create a separate home partition see here

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Bluecube on 2007-05-31
Thanks both for the help. Am I right in thinking that if I backup  my Home directory (or more elegantly have a Home partition) along with my etc directory and apt cache, then I can resintall the same version of Linux restore the three directories and I'll be back to where I started? That sounds too easy...

---

### Post by pbw on 2007-05-31
and to install all your old packages (if you've never cleaned cache), after you restore the cache just run sudo dpkg -i /var/cache/apt/archives/* ;) Never tried it, but i cant see why it wouldnt work. If there's an old and newer version of a package in the cache, it'd end up installing both, but the new second and overwrite/upgrade the old.

-- pbw

---

