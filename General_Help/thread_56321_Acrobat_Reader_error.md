---
title: "Acrobat Reader error"
date: 2005-08-12
forum: General Help
---

### Post by cnayak on 2005-08-12
I downloaded the Acrobat Reader using apt-get. Everything worked fine, but after the installation was over, Acrobat didn't open. I tried rebooting and clicking on the icon, still it didn't work. Any ideas about what went wrong?

---

### Post by heimo on 2005-08-12
Open terminal and type [i]acroread
[/i]
Any errors?

I would also try reinstalling:
sudo apt-get --purge remove *package_name*
sudo apt-get install [i]package_name

[/i]EDIT:* package_name* is probably acroread

---

### Post by cnayak on 2005-08-12
[QUOTE=heimo]Open terminal and type [i]acroread
[/i]
Any errors?

I would also try reinstalling:
sudo apt-get --purge remove *package_name*
sudo apt-get install [i]package_name

[/i]EDIT:* package_name* is probably acroread[/QUOTE]

 Here's what I get on typing acroread: 
 
 /usr/bin/acroread: line 12: /usr/lib/Acrobat5/bin/acroread: No such file or directory

---

### Post by Joshua Swink on 2005-08-15
[QUOTE=cnayak]Here's what I get on typing acroread: 
 
 /usr/bin/acroread: line 12: /usr/lib/Acrobat5/bin/acroread: No such file or directory[/QUOTE]
 I think the Adobe Reader package is broken. Here's what I did to fix it:

[INDENT][FONT=Courier New]
cd /usr/lib/Acrobat5/bin
mv acroread.sh acroread
vi acroread[/FONT][/INDENT]

You just have to change one line (hard to miss):

[INDENT][FONT=Courier New]
install_dir=/usr/lib/Acrobat5/Reader[/FONT][/INDENT]

---

### Post by rgrig on 2005-10-13
Thanks. That worked for me.

---

