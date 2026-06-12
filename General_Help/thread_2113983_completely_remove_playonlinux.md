---
title: "completely remove playonlinux"
date: 2013-02-08
forum: General Help
---

### Post by rilesac on 2013-02-08
How can I completely remove playonlinux including wine and everything that playonlinux installed on my computer?

I saw a post asking the same, the answers was: "delete the <home/.playonlinux>" is that going to delete everything?

Or I need to do something else?

Thanks & Greetings!

---

### Post by GameX2 on 2013-02-08
To uninstall PlayOnLinux, open a Terminal (CTRL-ALT-T):

```
sudo apt-get remove playonlinux
```Also delete the .PlayOnLinux folder in your Home (Hidden folder.  Press CTRL-H to display), this delete the configuration.  Also delete the .Wine folder.

To delete Wine, it depend on your version number, in my case, it would be:

```
sudo apt-get remove wine1.4
```

To check your Wine version, type "Wine" in your Unity dash, choose "Configure Wine".  Then open the "About" tab.  You'll see your version number.
If you have Ubuntu-Tweak or Synaptic installed, you might want to use the Cleaner to clean the useless stuff that might still be in Ubuntu.

Good luck

---

### Post by prismctg on 2013-02-08
try this
```
sudo apt-get purge playonlinux
```

---

### Post by GameX2 on 2013-02-09
> **prismctg said:**
> try this
```
sudo apt-get purge playonlinux
```

Thanks, I still don't remember the command line, yet.

---

