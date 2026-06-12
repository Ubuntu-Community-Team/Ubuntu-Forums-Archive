---
title: "trying to install wine"
date: 2019-09-06
forum: General Help
---

### Post by Hotchilli on 2019-09-06
here is the error when installing wine

Fetched 105 MB in 4min 46s (366 kB/s)                                          
E: Failed to fetch [http://mm.archive.ubuntu.com/ubuntu/pool/main/libo/libogg/libogg0_1.3.2-1_i386.deb](http://mm.archive.ubuntu.com/ubuntu/pool/main/libo/libogg/libogg0_1.3.2-1_i386.deb)  504  Gateway Time-out [IP: 91.189.88.173 80]
E: Failed to fetch [http://mm.archive.ubuntu.com/ubuntu/pool/main/libx/libxxf86vm/libxxf86vm1_1.1.4-1_i386.deb](http://mm.archive.ubuntu.com/ubuntu/pool/main/libx/libxxf86vm/libxxf86vm1_1.1.4-1_i386.deb)  504  Gateway Time-out [IP: 91.189.88.173 80]
E: Failed to fetch [http://mm.archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libcom-err2_1.44.6-1_i386.deb](http://mm.archive.ubuntu.com/ubuntu/pool/main/e/e2fsprogs/libcom-err2_1.44.6-1_i386.deb)  504  Gateway Time-out [IP: 91.189.88.173 80]
E: Failed to fetch [http://mm.archive.ubuntu.com/ubuntu/pool/main/libc/libcap2/libcap2_2.25-2_i386.deb](http://mm.archive.ubuntu.com/ubuntu/pool/main/libc/libcap2/libcap2_2.25-2_i386.deb)  504  Gateway Time-out [IP: 91.189.88.173 80]
E: Failed to fetch [http://mm.archive.ubuntu.com/ubuntu/pool/main/libf/libffi/libffi6_3.2.1-9_i386.deb](http://mm.archive.ubuntu.com/ubuntu/pool/main/libf/libffi/libffi6_3.2.1-9_i386.deb)  504  Gateway Time-out [IP: 91.189.88.173 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
:o

---

### Post by kc1di on 2019-09-06
Looks like your mirror is timing out, if Possible try a different Mirror. 
This [web page ]("http://www.ubuntubuzz.com/2018/03/how-to-change-ubuntu-repository-mirror-sources.html")can help you do that.

---

