---
title: "Getting man-db errors when installing a program"
date: 2018-08-25
forum: General Help
---

### Post by waltd on 2018-08-25
Hi all, I have Ubuntu 18.04.1 installed with Gnome. I did a clean install of 18.04.1 from scratch. Sometimes when I'm installing a program the terminal gets into an error message loop.  The error message will loop for a minute or so then it quits. The program I'm installing seems to install ok, but I would like to resolve this error message. I tried sudo apt install --reinstall man-db, but it didn't fix the problem. The error is related to man-db. Here is a copy of some of the error messages. I would appreciate any help to solve this error. 
       
/usr/bin/mandb: zcat< /usr/share/man/man1/git-revert.1.gz: Bad system call (coredumped)
/usr/bin/mandb:/usr/lib/man-db/manconv -f UTF-8:ISO-8859-1 -t UTF-8//IGNORE -q: Badsystem call (core dumped)
/usr/bin/mandb: zcat< /usr/share/man/man1/git-rm.1.gz: Bad system call (core dumped)
/usr/bin/mandb:zcat: Bad system call (core dumped)
/usr/bin/mandb: zcat< /usr/share/man/man1/git-rm.1.gz: Bad system call (core dumped)
/usr/bin/mandb:/usr/lib/man-db/manconv -f UTF-8:ISO-8859-1 -t UTF-8//IGNORE -q: Badsystem call (core dumped)
/usr/bin/mandb: zcat< /usr/share/man/man1/git-send-pack.1.gz: Bad system call (coredumped)
/usr/bin/mandb:zcat: Bad system call (core dumped)
/usr/bin/mandb: zcat< /usr/share/man/man1/git-send-pack.1.gz: Bad system call (coredumped)
/usr/bin/mandb:/usr/lib/man-db/manconv -f UTF-8:ISO-8859-1 -t UTF-8//IGNORE -q: Badsystem call (core dumped)
/usr/bin/mandb: zcat< /usr/share/man/man1/git-sh-i18n--envsubst.1.gz: Bad system call(core dumped)
/usr/bin/mandb:zcat: Bad system call (core dumped)
/usr/bin/mandb: zcat< /usr/share/man/man1/git-sh-i18n--envsubst.1.gz: Bad system call(core dumped)
/usr/bin/mandb:/usr/lib/man-db/manconv -f UTF-8:ISO-8859-1 -t UTF-8//IGNORE -q: Badsystem call (core dumped)

---

