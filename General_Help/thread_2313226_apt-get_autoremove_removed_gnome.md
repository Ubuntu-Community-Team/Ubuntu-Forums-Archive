---
title: "apt-get autoremove removed gnome*"
date: 2016-02-10
forum: General Help
---

### Post by Mark_in_Hollywood on 2016-02-10
While removing libreoffice with:

```
sudo apt-get remove --purge libreoffice-core
```

so as to cleanly install OpenOffice instead of LO, the terminal suggested running autoremove:

```
mark@Lexington:~$ sudo apt-get remove --purge libreoffice-core
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libreoffice-l10n-en-gb libreoffice-l10n-zh-cn
Use 'apt-get autoremove' to remove them.
```

I ran the autoremove and it seemed to have changed much more than purging the 2 libreoffice packages, above. The full list is at:

[http://pastebin.com/yFz96XD6](http://pastebin.com/yFz96XD6)

and what do I need to do to reinstall the gnome packages, before I reboot and no longer have a computer?

---

### Post by ian-weisser on 2016-02-10
Simply reinstalling the 'gnome' metapackage should pull in most of what you want to retain.

---

### Post by Mark_in_Hollywood on 2016-02-10
Thanks. Marking it as closed.

---

