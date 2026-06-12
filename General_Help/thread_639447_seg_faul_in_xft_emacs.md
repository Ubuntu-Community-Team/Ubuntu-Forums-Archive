---
title: "seg faul in xft emacs"
date: 2007-12-13
forum: General Help
---

### Post by maindoor on 2007-12-13
Hi,
    This post talks about a seg fault in emacs xft branch ?
    All of a sudden I get a seg fault like this 

    Fatal error (11)Segmentation fault (core dumped)

    This page talks about it, but no one has replied.
    [http://ubuntuforums.org/showthread.php?t=126023&page=9](http://ubuntuforums.org/showthread.php?t=126023&page=9)
    
    This is such a beautiful thing, this emacs with xft. beauty and power go hand in
    hand. But it is really annoying when it crashes suddenly. I built it like this.

# cvs -z3 -d:pserver:anonymous@cvs.savannah.gnu.org:/sources/emacs co -r  emacs-unicode-2 emacs 
# cd emacs/
# cvs up -Pd -r XFT_JHD_BRANCH 
# tla register-archive [email]jerome@debian.org[/email]--2006 [http://people.debian.org/~jerome/arch/jerome@debian.org--2006/](http://people.debian.org/~jerome/arch/jerome@debian.org--2006/)
# tla get -A [email]jerome@debian.org[/email]--2006 emacs-snapshot-debian--main

make bootstrap 
sudo ./configure --with-gtk=yes --enable-font-backend --with-xft=yes --prefix=/opt/xftemacs
make & make install

cat ~/.Xresources
Emacs*FontBackend: xft
Emacs.font: -*-Consolas-normal-r-*-*-16-*-*-*-c-*-iso8859-1
Xft.dpi: 96
Xft.hinting: None

and then just emacs brings up the beauty. But it crashes like murphy said.
Am I missing something here ?

Regards,
Maindoor.

---

