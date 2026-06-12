---
title: "try to install perl-support for gvim"
date: 2008-07-01
forum: General Help
---

### Post by perlsyntax on 2008-07-01
Can't stat /usr/local/share/perl/5.8.8: No such file or directory
at /home/perlsyntax/.vim/perl-support/scripts/pmdesc3.pl line 243
Can't stat /usr/local/lib/perl/5.8.8: No such file or directory
at /home/perlsyntax/.vim/perl-support/scripts/pmdesc3.pl line 243
Can't stat /usr/local/lib/site_perl: No such file or directory
at /home/perlsyntax/.vim/perl-support/scripts/pmdesc3.pl line 243
Can't cd to (./) .dbus: Permission denied
at /home/perlsyntax/.vim/perl-support/scripts/pmdesc3.pl line 243


i not sure why i can't find them dir when install perl-support for gvim.

---

### Post by soccerboy on 2008-07-01
it seems that this script is looking in the wrong directory for perl modules.  Maybe update their directories.

---

### Post by perlsyntax on 2008-07-01
how do i do i update the dir?

---

### Post by soccerboy on 2008-07-01
how are you trying to install perl-support? apt-get?

---

### Post by perlsyntax on 2008-07-01
i downloading it from vim.

---

### Post by soccerboy on 2008-07-01
never mind.  I don't even have gvim in synaptic.

---

### Post by perlsyntax on 2008-07-01
what should i do?

---

### Post by soccerboy on 2008-07-01
I am not positive but you might just be able to go to /home/perlsyntax/.vim/perl-support/scripts/pmdesc3.pl and change the paths.  What they are supposed to be, I am not quite positive.  It looks like local is extra in all those paths but don't take my word on it.  Wait for someone else to confirm.

---

### Post by perlsyntax on 2008-07-02
you sure it not a broken script?

---

### Post by perlsyntax on 2008-09-13
How do i update the dir in vim?

---

