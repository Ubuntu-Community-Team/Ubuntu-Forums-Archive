---
title: "Uninstall Conky-Manager"
date: 2014-02-01
forum: General Help
---

### Post by Shadius on 2014-02-01
Hey Everyone,

I installed conky-manager via the Ubuntu Software Center and when I uninstalled it, I still see a folder that says "conky-manager". My question is why is it still there and how do I properly remove it? Do I just click on it and delete it? Thanks for the help.

---

### Post by deadflowr on 2014-02-01
Is it in your home folder?
Then just delete it.

---

### Post by Shadius on 2014-02-01
Yes, it's in my **Home** folder. I was wondering why it was still staying there after I've uninstalled *conky-manager* though.

---

### Post by vasa1 on 2014-02-01
Folders created by applications may reside in your system (outside your home folder) or in your home folder. Using the Software Center to "uninstall" software, removes just the software but none of the additional configuration files (inside or outside your home).

If you use the command-line, you can ask for the config files outside your home to be deleted along with the package itself by running *sudo apt-get purge package_name*.

You can see the difference by using the *-s* option (where *-s* ensures that just a simulation is run). So, for any package you already have installed, run *apt-get remove -s package_name* and *apt-get purge -s package_name* and compare the items that are proposed to be removed by each. (*Sudo* isn't needed when the *-s* option is used.)

There's no way that I know of to tell apt-get to remove application files or folders from your home. You need to do that yourself.

---

### Post by Shadius on 2014-02-01
> **vasa1 said:**
> Folders created by applications may reside in your system (outside your home folder) or in your home folder. Using the Software Center to "uninstall" software, removes just the software but none of the additional configuration files (inside or outside your home).

If you use the command-line, you can ask for the config files outside your home to be deleted along with the package itself by running *sudo apt-get purge package_name*.

You can see the difference by using the *-s* option (where *-s* ensures that just a simulation is run). So, for any package you already have installed, run *apt-get remove -s package_name* and *apt-get purge -s package_name* and compare the items that are proposed to be removed by each. (*Sudo* isn't needed when the *-s* option is used.)

There's no way that I know of to tell apt-get to remove application files or folders from your home. You need to do that yourself.

Ahhh, I see. Thank you very much for that explanation. I was wondering how I could use the command-line to uninstall software and their configuration files. Much appreciated.

---

