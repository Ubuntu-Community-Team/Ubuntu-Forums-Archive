---
title: "removing ALL GnuCash data"
date: 2007-07-22
forum: General Help
---

### Post by gwatts on 2007-07-22
Ubuntu 7.04

I am trying to uninstall/remove  gnucash  in order to reinstall and import a different QIF file but after uninstalling and reinstalling gnucash it automatically loads the old data and entries.

Is there an easier way to totally remove a file or where is this old data so I might totally remove it. 

Why is it still on my computer after a apt-get remove?

Thank you.

---

### Post by MoLE on 2007-07-23
I suspect gnucash stores it's data files in your home directory.  When you do a purge or remove of any package - all it does it remove the program itself - it leaves the data alone (which is sane, as you may want to keep it).

Open up your home folder under Places --> home folder, then press Ctrl-H - this will reveal the hidden directories in your home folder.  If you delete your .gnucash directory, you can be pretty sure then when you install it next, then you will have a clean database to import into.

---

### Post by gwatts on 2007-07-24
MoLE

Thank you.

Unfortunately this does not solve my problem, the data persists after deleting .gnucash.

On only one occasion I also removed .gconfig (or perhaps only the gnucash files which were in .gconfig) (they 
were there only on the 1 occasion).

Now after multiple installs and removes, (including deleting .gnucash) the data still comes up in gnucash. On these multiple removes the gnucash files that were in .gnucash were not in .gconfig.

Perhaps there is a way to delete this file from gnucash while it is running?

An other suggestions will be appreciated.

---

