---
title: "Too many open files error while building Firefox source"
date: 2013-03-13
forum: General Help
---

### Post by kashinj on 2013-03-13
Hi,

I'm using ubuntuon DellXPS latop.
my environment:
XPS-M1330 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux

While building firefox browser using source code, I get too many files open error and exits.

============================================================
make -f client.mk build
/home/jayachandra/Firefox_release/mozilla/build/autoconf/mozconfig2client-mk: 59: /home/jayachandra/Firefox_release/mozilla/build/unix/mozconfig.linux: 1: Too many open files
/home/jayachandra/Firefox_release/mozilla/build/autoconf/mozconfig2client-mk: 35: .: 1: Too many open files
/home/jayachandra/Firefox_release/mozilla/.mozconfig.mk:8: *** Fix above errors before continuing..  Stop.
=============================================================

some of the posts in "specialised server community post" i found a post discussing similar issue for which solution has been provided in the IBM link [http://www-01.ibm.com/support/docview.wss?uid=swg21403391](http://www-01.ibm.com/support/docview.wss?uid=swg21403391).
This idea did n't work for me.

I tried building using 'root' access.
increased ulimit -n to more than 65536 to 100000 and 300000 still the same error.

here are the current values of limits in my setup
*# ulimit -n*
65539
*# sysctl -a | grep -i file*
fs.file-max = 308629
fs.file-nr = 7648	0	308629

but syslog has some entries like
Mar 14 08:44:01 jayachandra-XPS-M1330 kernel: [ 1385.638461] VFS: file-max limit 308629 reached
Mar 14 08:44:03 jayachandra-XPS-M1330 kernel: [ 1388.140514] VFS: file-max limit 308629 reached


I tried after closed some applications like "calibre" ebook reader.
only opened chrome browser (20tabs) and few terminal windows, 


even lsof having error in finding open files:
*#lsof | wc -l*
lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/jayachandra/gvfs
      Output information may be incomplete.
[B]output: 65010  <<<< still to read max limit.

[/B][B]just a mere opening chrome browser and few terminals should n't consume so many open files
[/B][B]
any help in increasing ulimit beyond system max 308629 and user limit 65540?
if i increase root user ulimit -n to beyond 65540 then system response will be degraded.

best regards,
viswanath





[/B]

---

### Post by kashinj on 2013-03-14
I tried this after rebooting with only terminal windows
set ulimit -n 65536.
Still I get the same error.

need help.

best regards,
Viswanath

---

### Post by mörgæs on 2013-03-15
Moved to General Help as this is not specific to Dell.

Why are you building Firefox rather than just installing it from the repository?

---

### Post by rnerwein on 2013-03-16
hi
try: sudo /bin/bash
then run: for i in `ls -d /proc/[0-9]*/fd`; do echo "----> $i `ls $i | wc -l`"; done | sort -rn --key=3 | more
to figure out the initiator of the wasted file-descriptors. --> ps -ef | grep PID_OF_THE_FIRST_TASK
ciao

p.s.: lsof: WARNING: can't stat() fuse.gvfsd-fuse file system /run/user/jayachandra/gvfs this is normal ;-)

---

