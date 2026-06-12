---
title: "Kolivas' Patchset for Kernel"
date: 2014-08-25
forum: General Help
---

### Post by dunbrokin on 2014-08-25
While following the instructions here for compiling the kernel,

[http://www.maketecheasier.com/speed-up-linux-computer/](http://www.maketecheasier.com/speed-up-linux-computer/)

I get the following message at the end.

make[2]: Entering directory `/home/hp/.tmp/kernel-ck-ubuntu-3.15.5/linux-3.15.5-ck1'
sh /home/hp/.tmp/kernel-ck-ubuntu-3.15.5/linux-3.15.5-ck1/arch/x86/boot/install.sh 3.15.5-ck1 arch/x86/boot/bzImage \
		System.map "/home/hp/.tmp/kernel-ck-ubuntu-3.15.5/linux-3.15.5-ck1/debian/linux-image-3.15.5-ck1//boot"
make[2]: Leaving directory `/home/hp/.tmp/kernel-ck-ubuntu-3.15.5/linux-3.15.5-ck1'
make[1]: Leaving directory `/home/hp/.tmp/kernel-ck-ubuntu-3.15.5/linux-3.15.5-ck1'
------------------------------------- DONE -------------------------------------
[+] copying debs files ...
    $ cp -- ../linux-*.deb /tmp 
cp: cannot stat ‘../linux-*.deb’: No such file or directory

real	624m30.258s
user	537m55.757s
sys	80m18.383s
hp@hp:/tmp$

Where should I go from here?

---

### Post by mc4man on 2014-08-25
If you go to the bottom of the page you linked there seems to be a similar report about the .deb's failing to be created (or possibly failing to be created, did you check?

Otherwise maybe try one or more of the precompiled .debs, seem to be ok here (did produce some odd messages during install with dpkg

---

### Post by dunbrokin on 2014-08-25
Thanks for that. I used the recompiled ones and they worked......I would not say that the machine was noticeably faster to be honest!

---

### Post by mc4man on 2014-08-25
> **dunbrokin said:**
> Thanks for that. I used the recompiled ones and they worked......I would not say that the machine was noticeably faster to be honest!
I can't say there is any noticeable improvement either, in the somewhat distant past when I used the ck patches didn't then either.

(- though after installing in a multiboot machine the cpu use of mpv went back to where it was some time ago, can't see the connection yet. 16 - 17%  to 5 - 6% on same file using vaapi .. weird.

---

