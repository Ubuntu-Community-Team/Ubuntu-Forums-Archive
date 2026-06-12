---
title: "[SOLVED] Items won't delete from trash"
date: 2008-05-11
forum: General Help
---

### Post by Hooya on 2008-05-11
I installed syncegnome based on the instructions on this site:
[http://www.synce.org/moin/SynceTools/SynceGnome](http://www.synce.org/moin/SynceTools/SynceGnome)
and don't need it installed anymore.  I can't figure out how to "uninstall" this program, but at least wanted the folder out of my home directory.  The problem is I can't delete it from the trash.  The command "rm -rf ~/.Trash/*" does not work, I get the error

rm: cannot remove `/home/hooya/.Trash/*': No such file or directory

So I have no idea how to delete the folder from the trash.  Any ideas?  On Hardy x64.

Ah, found this through more google searches.  For anyone that finds this later:
sudo rm -rf ~/.local/share/Trash/files/*
is the command in hardy.

---

### Post by russo.mic on 2008-05-12
mark the thread as solved, this comes up often.

Russo

---

### Post by johnhammonds on 2009-01-20
> **Hooya said:**
> Ah, found this through more google searches.  For anyone that finds this later:
sudo rm -rf ~/.local/share/Trash/files/*
is the command in hardy.

Awesome! Worked for me! ;-)

---

### Post by spartan_87 on 2009-01-20
Sweet it works. Iv had a folder in my trash that I couldn't delete for a long time and just forgot about it until I saw this. Thanks!

---

