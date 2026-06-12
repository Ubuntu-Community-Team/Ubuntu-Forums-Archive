---
title: "libc-2.2.3.so ,crt1.o.... : No such file or Directory"
date: 2008-05-20
forum: General Help
---

### Post by leo83 on 2008-05-20
Hello,

I get following errors for the following file when it is compiled..

[http://pastebin.com/d9311105](http://pastebin.com/d9311105)

[HTML]make[2]: Entering directory `/srv/krone/Mini-Controller/Codebase 2.5.0.0/PoE/lib_source/tool_libs'
cd /usr/lib32;find crt1.o crti.o crtn.o gcrt1.o Mcrt1.o  libc-2.2.3.so libcrypt-2.2.3.so libcrypt.so libcrypt.so.1 libc.so libc.so.6 libdl-2.2.3.so libdl.so libdl.so.2 libm-2.2.3.so libm.so libm.so.6 libnsl-2.2.3.so libnsl.so libnsl.so.1 libnss_compat-2.2.3.so libnss_compat.so libnss_compat.so.2 libnss_dns-2.2.3.so libnss_dns.so libnss_dns.so.2 libnss_files-2.2.3.so libnss_files.so libnss_files.so.2 libnss_hesiod-2.2.3.so libnss_hesiod.so libnss_hesiod.so.2 libnss_nis-2.2.3.so libnss_nisplus-2.2.3.so libnss_nisplus.so libnss_nisplus.so.2 libnss_nis.so libnss_nis.so.2 libpthread-0.9.so libpthread.so libpthread.so.0 libresolv-2.2.3.so libresolv.so libresolv.so.2 libutil-2.2.3.so libutil.so libutil.so.1 libz.so libz.so.1 libz.so.1.2.1 libc_nonshared.a libthread_db-1.0.so  libthread_db.so  libthread_db.so.1 libssl.so.0.9.8 libssl.so libcrypto.so.0.9.8 libcrypto.so libz.so libz.so.1 libz.so.1.2.1 libexpat.so libexpat.so.0 libexpat.so.0.5.0 | cpio -pdmu /srv/krone/Mini-Controller/Codebase 2.5.0.0/PoE/lib_source/tool_libs;cd /srv/krone/Mini-Controller/Codebase 2.5.0.0/PoE/lib_source/tool_libs
find: crt1.o: No such file or directory
find: crti.o: No such file or directory
find: crtn.o: No such file or directory
find: gcrt1.o: No such file or directory
find: Mcrt1.o: No such file or directory
find: libc-2.2.3.so: No such file or directory
find: libcrypt-2.2.3.so: No such file or directory
find: libcrypt.so: No such file or directory
find: libcrypt.so.1: No such file or directory
find: libc.so: No such file or directory
find: libc.so.6: No such file or directory
find: libdl-2.2.3.so: No such file or directory
find: libdl.so: No such file or directory
find: libdl.so.2: No such file or directory
find: libm-2.2.3.so: No such file or directory
find: libm.so: No such file or directory
find: libm.so.6: No such file or directory
find: libnsl-2.2.3.so: No such file or directory
find: libnsl.so: No such file or directory
find: libnsl.so.1: No such file or directory
find: libnss_compat-2.2.3.so: No such file or directory
find: libnss_compat.so: No such file or directory
find: libnss_compat.so.2: No such file or directory
find: libnss_dns-2.2.3.so: No such file or directory
find: libnss_dns.so: No such file or directory
find: libnss_dns.so.2: No such file or directory
find: libnss_files-2.2.3.so: No such file or directory
find: libnss_files.so: No such file or directory
find: libnss_files.so.2: No such file or directory
find: libnss_hesiod-2.2.3.so: No such file or directory
find: libnss_hesiod.so: No such file or directory
find: libnss_hesiod.so.2: No such file or directory
find: libnss_nis-2.2.3.so: No such file or directory
find: libnss_nisplus-2.2.3.so: No such file or directory
find: libnss_nisplus.so: No such file or directory
find: libnss_nisplus.so.2: No such file or directory
find: libnss_nis.so: No such file or directory
find: libnss_nis.so.2: No such file or directory
find: libpthread-0.9.so: No such file or directory
find: libpthread.so: No such file or directory
find: libpthread.so.0: No such file or directory
find: libresolv-2.2.3.so: No such file or directory
find: libresolv.so: No such file or directory
find: libresolv.so.2: No such file or directory
find: libutil-2.2.3.so: No such file or directory
find: libutil.so: No such file or directory
find: libutil.so.1: No such file or directory
find: libz.so: No such file or directory
find: libz.so.1.2.1: No such file or directory
find: libc_nonshared.a: No such file or directory
find: libthread_db-1.0.so: No such file or directory
find: libthread_db.so: No such file or directory
find: libthread_db.so.1: No such file or directory
find: libssl.so: No such file or directory
find: libcrypto.so: No such file or directory
find: libz.so: No such file or directory
find: libz.so.1.2.1: No such file or directory
find: libexpat.so: No such file or directory
find: libexpat.so.0: No such file or directory
find: libexpat.so.0.5.0: No such file or directory[/HTML]

Whats going wrong here ? some of the files are existing in /usr/bin but most of them not..Which package do i need to download , so i its error free..

Thanks

---

### Post by leo83 on 2008-05-20
Solved it!!
changed the path and works fine now.. I am getting over Linux ;-)

---

### Post by agni07 on 2011-10-28
I am facing a similar problem.

What path did you change for it to work??

---

### Post by oldos2er on 2011-10-28
Closed. Please start a new thread for your question.

---

