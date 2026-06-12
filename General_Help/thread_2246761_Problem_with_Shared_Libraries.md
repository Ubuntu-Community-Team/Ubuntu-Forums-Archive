---
title: "Problem with Shared Libraries"
date: 2014-10-03
forum: General Help
---

### Post by Jasper_Haller on 2014-10-03
Hello all,

I cannot open LibreOffice and the Software Center, though I suspect the problem extends to other applications, as well. Opening a terminal and trying to start LibreOffice, I obtain the following error message:

> 
/usr/lib/libreoffice/program/soffice.bin: error while loading shared libraries: libxslt.so.1: cannot open shared object file: No such file or directory


I've done some googling, but found nothing that helped me. [This]("http://askubuntu.com/questions/478109/libxslt-so-1-cannot-open-shared-object-file-while-trying-to-load-libreoffice") stackexchange post seemingly refers to the same problem, but there are no answers.

I would appreciate any pointers.

---

### Post by steeldriver on 2014-10-03
What version of Ubuntu are you running, and is it 64-bit or 32-bit?

---

### Post by matt_symes on 2014-10-03
Hi

Open a termminal and type

```
sudo updatedb
```

Enter your password. It will not be echoed to the screen. It will take a moment to complete and will facilitate a quick and up to date search.

Then type

```
locate libxslt.so.1
```

Post the output of the above command into your next post.

Post the output of these commands as well.

```
uname -m
```
```
cat /etc/lsb-release
```

That way we'll know what you have installed and where you are in relation to the library file.

Kind regards

---

### Post by Jasper_Haller on 2014-10-03
Thanks for your quick replies. The output from the *locate* command is
```
 
/usr/lib/i386-linux-gnu/libxslt.so.1
/usr/lib/i386-linux-gnu/libxslt.so.1.1.28

```

The output from *uname* is
```

x86_64

```

And the output from *cat* is
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"

```

Hope this is useful. Thanks for your help!

---

### Post by matt_symes on 2014-10-03
Hi

> **Jasper_Haller said:**
> Thanks for your quick replies. The output from the *locate* command is
```
 
/usr/lib/i386-linux-gnu/libxslt.so.1
/usr/lib/i386-linux-gnu/libxslt.so.1.1.28

```

The output from *uname* is
```

x86_64

```

And the output from *cat* is
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.1 LTS"

```


You're running a 64-bit kernel but you only have the 32 bit libxslt.so.1 library by the looks of it and i suspect software-center and libreoffice are looking for the 64bit version.

Can we double check that just to confirm.

Please post the output of these commands.

```
getconf LONG_BIT
```

```
grep lm /proc/cpuinfo
```

```
ls -d /usr/lib/x86_64-linux-gnu/
```

```
ldd /usr/lib/libreoffice/program/soffice.bin | grep libxslt.so.1
```

Kind regards

---

### Post by Jasper_Haller on 2014-10-03
Here you go. Output from *getconf*:
```
64
```

Output from *grep*:
```
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 fma cx16 xtpr pdcm pcid sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid
```

Output from *ls*:
```
/usr/lib/x86_64-linux-gnu/
```

Output from *ldd*:
```
libxslt.so.1 => not found
```

Is this what you expected?

---

### Post by matt_symes on 2014-10-03
Hi

> **Jasper_Haller said:**
> 
Output from *ls*:
```
/usr/lib/x86_64-linux-gnu/
```

Output from *ldd*:
```
libxslt.so.1 => not found
```

Is this what you expected?

Yep. Pretty much what i expected.

Just one last command to eliminate all doubt. Please post the output of

```
file /usr/lib/libreoffice/program/soffice.bin
```

I would expect it to say 64  bit in the output somewhere.

I have to pop out for a couple of hours but just a couple of questions first.

When did this start happening ?
Did you install/update/remove any software packages at the time it happened ?

We can continue this when i get back unless someone else helps.

Kind regards

---

### Post by Jasper_Haller on 2014-10-03
Hi,

many thanks for your help. Just as you thought, the output of the command you posted mentions 64-bit:

```
/usr/lib/libreoffice/program/soffice.bin: ELF 64-bit LSB  executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=1a282ca759a3763b8b18a2159579be8967af83b4, stripped
```

As for your other questions,

> 
When did this start happening ?
Did you install/update/remove any software packages at the time it happened ?


This started happening this morning. The software had been running without a problem until that point. I do not recall installing or removing any software, but I have been running ```
apt-get update
``` and ```
apt-get upgrade
``` frequently recently, and it has resulted in a bunch of updates. Nothing looked out of the ordinary to me, but then again, I'm not an experienced user.

One thing that I probably should have mentioned earlier is that, the first time this happened, I got two error messages. One is the one I mentioned in my first post; the other informed me that I had no running Java Runtime Environment. I have been able to fix that by installing the packages *openjdk-7-jre* and *openjdk-7-jre-headless*.

---

### Post by matt_symes on 2014-10-03
Hi

I'm back. I was quicker than i suspected.

Anyway, on my laptop the libxslt.so.1 symlink pointing to the correct libxslt library is provided by the package libxslt1.1.
```

matthew-laptop:/home/matthew:0 % apt-file search libxslt.so.1  
libxslt1.1: /usr/lib/x86_64-linux-gnu/libxslt.so.1
libxslt1.1: /usr/lib/x86_64-linux-gnu/libxslt.so.1.1.28
matthew-laptop:/home/matthew:0 %
```

On my 64 bit machine it's installed from the libxslt.1.1:amd64 package.

```
matthew-laptop:/home/matthew:0 % dpkg -l libxslt1.1
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                        Version            Architecture       Description
+++-===========================-==================-==================-============================================================
ii  libxslt1.1:amd64            1.1.28-2build1     amd64              XSLT 1.0 processing library - runtime library
matthew-laptop:/home/matthew:0 %
```

If you run the above dpkg command on your machine, you should see libxslt1.1:i386 as the package name.

Anyway, we could attempt to install the 64 bit version of the package but i think it may be a really good idea to see if we can identify why the 64bit version was uninstalled. 

If you agree and are prepared to investigate then please post the output of

```
zgrep libxslt1.1 /var/log/dpkg.log*
```

This should give us the time it was uninstalled and we can take it from there.

Kind regards

---

### Post by Jasper_Haller on 2014-10-03
> If you run the above dpkg command on your machine, you should see libxslt1.1:i386 as the package name.

I do.

> 
Anyway, we could attempt to install the 64 bit version of the package  but i think it may be a really good idea to see if we can identify why  the 64bit version was uninstalled. 

If you agree and are prepared to investigate then please post the output of

```
zgrep libxslt1.1 /var/log/dpkg.log*
```

This should give us the time it was uninstalled and we can take it from there.

Sure, why not. Here's the output:

```
/var/log/dpkg.log.5.gz:2014-05-03 00:27:39 upgrade libxslt1.1:amd64 1.1.28-2 1.1.28-2build1
/var/log/dpkg.log.5.gz:2014-05-03 00:27:39 status half-configured libxslt1.1:amd64 1.1.28-2
/var/log/dpkg.log.5.gz:2014-05-03 00:27:39 status unpacked libxslt1.1:amd64 1.1.28-2
/var/log/dpkg.log.5.gz:2014-05-03 00:27:39 status half-installed libxslt1.1:amd64 1.1.28-2
/var/log/dpkg.log.5.gz:2014-05-03 00:27:39 status half-installed libxslt1.1:amd64 1.1.28-2
/var/log/dpkg.log.5.gz:2014-05-03 00:27:39 status unpacked libxslt1.1:amd64 1.1.28-2build1
/var/log/dpkg.log.5.gz:2014-05-03 00:27:39 status unpacked libxslt1.1:amd64 1.1.28-2build1
/var/log/dpkg.log.5.gz:2014-05-03 00:35:57 configure libxslt1.1:amd64 1.1.28-2build1 <none>
/var/log/dpkg.log.5.gz:2014-05-03 00:35:57 status unpacked libxslt1.1:amd64 1.1.28-2build1
/var/log/dpkg.log.5.gz:2014-05-03 00:35:58 status half-configured libxslt1.1:amd64 1.1.28-2build1
/var/log/dpkg.log.5.gz:2014-05-03 00:35:58 status installed libxslt1.1:amd64 1.1.28-2build1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:09 install libxslt1.1:i386 <keine> 1.1.28-2build1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:09 status half-installed libxslt1.1:i386 1.1.28-2build1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:09 status unpacked libxslt1.1:i386 1.1.28-2build1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:09 status unpacked libxslt1.1:i386 1.1.28-2build1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:19 configure libxslt1.1:i386 1.1.28-2build1 <keine>
/var/log/dpkg.log.5.gz:2014-05-10 20:51:19 status unpacked libxslt1.1:i386 1.1.28-2build1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:19 status half-configured libxslt1.1:i386 1.1.28-2build1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:19 status installed libxslt1.1:i386 1.1.28-2build1
/var/log/dpkg.log.7.gz:2013-10-16 19:00:47 install libxslt1.1:amd64 <none> 1.1.28-2
/var/log/dpkg.log.7.gz:2013-10-16 19:00:47 status half-installed libxslt1.1:amd64 1.1.28-2
/var/log/dpkg.log.7.gz:2013-10-16 19:00:47 status unpacked libxslt1.1:amd64 1.1.28-2
/var/log/dpkg.log.7.gz:2013-10-16 19:00:47 status unpacked libxslt1.1:amd64 1.1.28-2
/var/log/dpkg.log.7.gz:2013-10-16 19:02:28 configure libxslt1.1:amd64 1.1.28-2 <none>
/var/log/dpkg.log.7.gz:2013-10-16 19:02:28 status unpacked libxslt1.1:amd64 1.1.28-2
/var/log/dpkg.log.7.gz:2013-10-16 19:02:28 status half-configured libxslt1.1:amd64 1.1.28-2
/var/log/dpkg.log.7.gz:2013-10-16 19:02:28 status installed libxslt1.1:amd64 1.1.28-2
```

Cheers,
Jasper

---

### Post by matt_symes on 2014-10-03
Hi

For later reference this command will install the 64bit version of libxslt1.1

```
sudo apt-get install libxslt1.1:amd64
```

For the moment, can you post the output of 

```
sudo apt-get install --assume-no libxslt1.1:amd64
```

```
zgrep "2014-05-10" /var/log/dpkg.log* | grep "status installed"
```

Kind regards

---

### Post by Jasper_Haller on 2014-10-05
Hi,

> For the moment, can you post the output of ```
sudo apt-get install --assume-no libxslt1.1:amd64
```

I get ```
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut.       
Statusinformationen werden eingelesen.... Fertig
libxslt1.1 ist schon die neueste Version.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 6 nicht aktualisiert.
```

Translation: libxslt1.1 is already the newest version, so nothing was updated. As for

> ```
zgrep "2014-05-10" /var/log/dpkg.log* | grep "status installed"
```

I get the following output:

```
/var/log/dpkg.log.5.gz:2014-05-10 12:52:15 status installed libselinux1:amd64 2.2.2-1ubuntu0.1
/var/log/dpkg.log.5.gz:2014-05-10 12:52:15 status installed libc-bin:amd64 2.19-0ubuntu6
/var/log/dpkg.log.5.gz:2014-05-10 12:52:23 status installed man-db:amd64 2.6.7.1-1
/var/log/dpkg.log.5.gz:2014-05-10 12:52:23 status installed gconf2:amd64 3.2.6-0ubuntu2
/var/log/dpkg.log.5.gz:2014-05-10 12:52:23 status installed bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 12:52:23 status installed desktop-file-utils:amd64 0.22-1ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 12:52:23 status installed gnome-menus:amd64 3.10.1-0ubuntu2
/var/log/dpkg.log.5.gz:2014-05-10 12:52:23 status installed mime-support:all 3.54ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 12:52:24 status installed libglib2.0-0:amd64 2.40.0-2
/var/log/dpkg.log.5.gz:2014-05-10 12:52:24 status installed ureadahead:amd64 0.100.0-16
/var/log/dpkg.log.5.gz:2014-05-10 12:52:25 status installed cups:amd64 1.7.2-0ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 12:52:25 status installed install-info:amd64 5.2.0.dfsg.1-2
/var/log/dpkg.log.5.gz:2014-05-10 12:52:26 status installed hicolor-icon-theme:all 0.13-1
/var/log/dpkg.log.5.gz:2014-05-10 12:52:26 status installed libasprintf0c2:amd64 0.18.3.1-1ubuntu3
/var/log/dpkg.log.5.gz:2014-05-10 12:52:26 status installed libasprintf-dev:amd64 0.18.3.1-1ubuntu3
/var/log/dpkg.log.5.gz:2014-05-10 12:52:26 status installed libavutil52:amd64 6:9.13-0ubuntu0.14.04.1
/var/log/dpkg.log.5.gz:2014-05-10 12:52:26 status installed libavcodec54:amd64 6:9.13-0ubuntu0.14.04.1
/var/log/dpkg.log.5.gz:2014-05-10 12:52:26 status installed libavformat54:amd64 6:9.13-0ubuntu0.14.04.1
/var/log/dpkg.log.5.gz:2014-05-10 12:52:26 status installed libavresample1:amd64 6:9.13-0ubuntu0.14.04.1
/var/log/dpkg.log.5.gz:2014-05-10 12:52:26 status installed libcupsfilters1:amd64 1.0.52-0ubuntu1.1
/var/log/dpkg.log.5.gz:2014-05-10 12:52:26 status installed libfontembed1:amd64 1.0.52-0ubuntu1.1
/var/log/dpkg.log.5.gz:2014-05-10 12:52:26 status installed libgettextpo0:amd64 0.18.3.1-1ubuntu3
/var/log/dpkg.log.5.gz:2014-05-10 12:52:26 status installed libgettextpo-dev:amd64 0.18.3.1-1ubuntu3
/var/log/dpkg.log.5.gz:2014-05-10 12:52:26 status installed libgexiv2-2:amd64 0.10.0-1ubuntu2
/var/log/dpkg.log.5.gz:2014-05-10 12:52:26 status installed libido3-0.1-0:amd64 13.10.0+14.04.20140423-0ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 12:52:26 status installed libswscale2:amd64 6:9.13-0ubuntu0.14.04.1
/var/log/dpkg.log.5.gz:2014-05-10 12:52:26 status installed iputils-ping:amd64 3:20121221-4ubuntu1.1
/var/log/dpkg.log.5.gz:2014-05-10 12:52:26 status installed gettext-base:amd64 0.18.3.1-1ubuntu3
/var/log/dpkg.log.5.gz:2014-05-10 12:52:26 status installed iputils-tracepath:amd64 3:20121221-4ubuntu1.1
/var/log/dpkg.log.5.gz:2014-05-10 12:52:27 status installed python3-update-manager:all 1:0.196.12
/var/log/dpkg.log.5.gz:2014-05-10 12:52:27 status installed update-manager-core:all 1:0.196.12
/var/log/dpkg.log.5.gz:2014-05-10 12:52:27 status installed update-manager:all 1:0.196.12
/var/log/dpkg.log.5.gz:2014-05-10 12:52:27 status installed cups-browsed:amd64 1.0.52-0ubuntu1.1
/var/log/dpkg.log.5.gz:2014-05-10 12:52:27 status installed cups-filters-core-drivers:amd64 1.0.52-0ubuntu1.1
/var/log/dpkg.log.5.gz:2014-05-10 12:52:28 status installed cups-filters:amd64 1.0.52-0ubuntu1.1
/var/log/dpkg.log.5.gz:2014-05-10 12:52:28 status installed gettext:amd64 0.18.3.1-1ubuntu3
/var/log/dpkg.log.5.gz:2014-05-10 12:52:29 status installed librhythmbox-core8:amd64 3.0.2-0ubuntu2
/var/log/dpkg.log.5.gz:2014-05-10 12:52:29 status installed gir1.2-rb-3.0:amd64 3.0.2-0ubuntu2
/var/log/dpkg.log.5.gz:2014-05-10 12:52:29 status installed iputils-arping:amd64 3:20121221-4ubuntu1.1
/var/log/dpkg.log.5.gz:2014-05-10 12:52:29 status installed nautilus:amd64 1:3.10.1-0ubuntu9
/var/log/dpkg.log.5.gz:2014-05-10 12:52:29 status installed rhythmbox-data:all 3.0.2-0ubuntu2
/var/log/dpkg.log.5.gz:2014-05-10 12:52:29 status installed unity-greeter:amd64 14.04.10-0ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 12:52:29 status installed libc-bin:amd64 2.19-0ubuntu6
/var/log/dpkg.log.5.gz:2014-05-10 20:47:48 status installed man-db:amd64 2.6.7.1-1
/var/log/dpkg.log.5.gz:2014-05-10 20:47:48 status installed bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:47:48 status installed desktop-file-utils:amd64 0.22-1ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:47:48 status installed gnome-menus:amd64 3.10.1-0ubuntu2
/var/log/dpkg.log.5.gz:2014-05-10 20:47:49 status installed mime-support:all 3.54ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:47:49 status installed gdebi-core:all 0.9.5.3ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:47:49 status installed gdebi:all 0.9.5.3ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:12 status installed man-db:amd64 2.6.7.1-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:13 status installed doc-base:all 0.10.5
/var/log/dpkg.log.5.gz:2014-05-10 20:51:13 status installed libglib2.0-0:amd64 2.40.0-2
/var/log/dpkg.log.5.gz:2014-05-10 20:51:13 status installed libexpat1:i386 2.1.0-4ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:13 status installed libffi6:i386 3.1~rc1+r3.0.13-12
/var/log/dpkg.log.5.gz:2014-05-10 20:51:13 status installed libgpg-error0:i386 1.12-0.2ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:13 status installed libgcrypt11:i386 1.5.3-2ubuntu4
/var/log/dpkg.log.5.gz:2014-05-10 20:51:13 status installed libp11-kit0:i386 0.20.2-2ubuntu2
/var/log/dpkg.log.5.gz:2014-05-10 20:51:13 status installed libtasn1-6:i386 3.4-3
/var/log/dpkg.log.5.gz:2014-05-10 20:51:13 status installed zlib1g:i386 1:1.2.8.dfsg-1ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:13 status installed libgnutls26:i386 2.12.23-12ubuntu2
/var/log/dpkg.log.5.gz:2014-05-10 20:51:13 status installed libsqlite3-0:i386 3.8.2-1ubuntu2
/var/log/dpkg.log.5.gz:2014-05-10 20:51:14 status installed libssl1.0.0:i386 1.0.1f-1ubuntu2.1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:14 status installed gcc-4.8-base:i386 4.8.2-19ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:14 status installed libstdc++6:i386 4.8.2-19ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:14 status installed libcomerr2:i386 1.42.9-3ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:14 status installed libdbus-1-3:i386 1.6.18-0ubuntu4
/var/log/dpkg.log.5.gz:2014-05-10 20:51:14 status installed libdrm2:i386 2.4.52-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:14 status installed libjson-c2:i386 0.11-3ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:14 status installed liblzma5:i386 5.1.1alpha+20120614-2ubuntu2
/var/log/dpkg.log.5.gz:2014-05-10 20:51:14 status installed libnih1:i386 1.0.3-4ubuntu25
/var/log/dpkg.log.5.gz:2014-05-10 20:51:14 status installed libnih-dbus1:i386 1.0.3-4ubuntu25
/var/log/dpkg.log.5.gz:2014-05-10 20:51:14 status installed libpcre3:i386 1:8.31-2ubuntu2
/var/log/dpkg.log.5.gz:2014-05-10 20:51:14 status installed libpng12-0:i386 1.2.50-1ubuntu2
/var/log/dpkg.log.5.gz:2014-05-10 20:51:14 status installed libselinux1:i386 2.2.2-1ubuntu0.1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:14 status installed libtinfo5:i386 5.9+20140118-1ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:14 status installed libcgmanager0:i386 0.24-0ubuntu5
/var/log/dpkg.log.5.gz:2014-05-10 20:51:15 status installed libudev1:i386 204-5ubuntu20
/var/log/dpkg.log.5.gz:2014-05-10 20:51:15 status installed libuuid1:i386 2.20.1-5.1ubuntu20
/var/log/dpkg.log.5.gz:2014-05-10 20:51:15 status installed libelf1:i386 0.158-0ubuntu5.1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:15 status installed libglib2.0-0:i386 2.40.0-2
/var/log/dpkg.log.5.gz:2014-05-10 20:51:15 status installed libkrb5support0:i386 1.12+dfsg-2ubuntu4
/var/log/dpkg.log.5.gz:2014-05-10 20:51:15 status installed libk5crypto3:i386 1.12+dfsg-2ubuntu4
/var/log/dpkg.log.5.gz:2014-05-10 20:51:15 status installed libkeyutils1:i386 1.5.6-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:15 status installed libkrb5-3:i386 1.12+dfsg-2ubuntu4
/var/log/dpkg.log.5.gz:2014-05-10 20:51:15 status installed libgssapi-krb5-2:i386 1.12+dfsg-2ubuntu4
/var/log/dpkg.log.5.gz:2014-05-10 20:51:15 status installed libxau6:i386 1:1.0.8-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:15 status installed libxdmcp6:i386 1:1.1.1-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:15 status installed libxcb1:i386 1.10-2ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:15 status installed libx11-6:i386 2:1.6.2-1ubuntu2
/var/log/dpkg.log.5.gz:2014-05-10 20:51:15 status installed libxext6:i386 2:1.3.2-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:15 status installed libxml2:i386 2.9.1+dfsg1-3ubuntu4
/var/log/dpkg.log.5.gz:2014-05-10 20:51:15 status installed libasound2:i386 1.0.27.2-3ubuntu7
/var/log/dpkg.log.5.gz:2014-05-10 20:51:15 status installed libsamplerate0:i386 0.1.8-7
/var/log/dpkg.log.5.gz:2014-05-10 20:51:15 status installed libjack-jackd2-0:i386 1.9.9.5+20130622git7de15e7a-1ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:16 status installed libasyncns0:i386 0.8-4ubuntu2
/var/log/dpkg.log.5.gz:2014-05-10 20:51:16 status installed libogg0:i386 1.3.1-1ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:16 status installed libflac8:i386 1.3.0-2
/var/log/dpkg.log.5.gz:2014-05-10 20:51:16 status installed libvorbis0a:i386 1.3.2-1.3ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:16 status installed libvorbisenc2:i386 1.3.2-1.3ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:16 status installed libsndfile1:i386 1.0.25-7ubuntu2
/var/log/dpkg.log.5.gz:2014-05-10 20:51:16 status installed libwrap0:i386 7.6.q-25
/var/log/dpkg.log.5.gz:2014-05-10 20:51:16 status installed libpulse0:i386 1:4.0-0ubuntu11
/var/log/dpkg.log.5.gz:2014-05-10 20:51:16 status installed libspeexdsp1:i386 1.2~rc1.1-1ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:16 status installed libasound2-plugins:i386 1.0.27-2ubuntu2
/var/log/dpkg.log.5.gz:2014-05-10 20:51:16 status installed libice6:i386 2:1.0.8-2
/var/log/dpkg.log.5.gz:2014-05-10 20:51:16 status installed libsm6:i386 2:1.2.1-2
/var/log/dpkg.log.5.gz:2014-05-10 20:51:16 status installed libxt6:i386 1:1.1.4-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:16 status installed libaudio2:i386 1.9.4-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:16 status installed libavahi-common-data:i386 0.6.31-4ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:16 status installed libavahi-common3:i386 0.6.31-4ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:16 status installed libavahi-client3:i386 0.6.31-4ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:16 status installed libcups2:i386 1.7.2-0ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:16 status installed libpciaccess0:i386 0.13.2-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:17 status installed libdrm-intel1:i386 2.4.52-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:17 status installed libdrm-nouveau2:i386 2.4.52-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:17 status installed libdrm-radeon1:i386 2.4.52-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:17 status installed libfreetype6:i386 2.5.2-1ubuntu2
/var/log/dpkg.log.5.gz:2014-05-10 20:51:17 status installed libfontconfig1:i386 2.11.0-0ubuntu4
/var/log/dpkg.log.5.gz:2014-05-10 20:51:17 status installed libllvm3.4:i386 1:3.4-1ubuntu3
/var/log/dpkg.log.5.gz:2014-05-10 20:51:17 status installed libgl1-mesa-dri:i386 10.1.0-4ubuntu5
/var/log/dpkg.log.5.gz:2014-05-10 20:51:17 status installed libglapi-mesa:i386 10.1.0-4ubuntu5
/var/log/dpkg.log.5.gz:2014-05-10 20:51:17 status installed libx11-xcb1:i386 2:1.6.2-1ubuntu2
/var/log/dpkg.log.5.gz:2014-05-10 20:51:17 status installed libxcb-dri2-0:i386 1.10-2ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:17 status installed libxcb-dri3-0:i386 1.10-2ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:17 status installed libxcb-glx0:i386 1.10-2ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:17 status installed libxcb-present0:i386 1.10-2ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:17 status installed libxcb-sync1:i386 1.10-2ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:17 status installed libxdamage1:i386 1:1.1.4-1ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:17 status installed libxfixes3:i386 1:5.0.1-1ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:17 status installed libxshmfence1:i386 1.1-2
/var/log/dpkg.log.5.gz:2014-05-10 20:51:17 status installed libxxf86vm1:i386 1:1.1.3-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:18 status installed libgl1-mesa-glx:i386 10.1.0-4ubuntu5
/var/log/dpkg.log.5.gz:2014-05-10 20:51:18 status installed libgstreamer1.0-0:i386 1.2.3-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:18 status installed liborc-0.4-0:i386 1:0.4.18-1ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:18 status installed libgstreamer-plugins-base1.0-0:i386 1.2.3-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:18 status installed libjpeg-turbo8:i386 1.3.0-0ubuntu2
/var/log/dpkg.log.5.gz:2014-05-10 20:51:18 status installed mysql-common:all 5.5.37-0ubuntu0.14.04.1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:18 status installed libmysqlclient18:i386 5.5.37-0ubuntu0.14.04.1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:18 status installed libqtcore4:i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4
/var/log/dpkg.log.5.gz:2014-05-10 20:51:18 status installed libqt4-xml:i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4
/var/log/dpkg.log.5.gz:2014-05-10 20:51:18 status installed libqtdbus4:i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4
/var/log/dpkg.log.5.gz:2014-05-10 20:51:18 status installed libqt4-network:i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4
/var/log/dpkg.log.5.gz:2014-05-10 20:51:18 status installed libqt4-script:i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4
/var/log/dpkg.log.5.gz:2014-05-10 20:51:18 status installed libqt4-sql:i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4
/var/log/dpkg.log.5.gz:2014-05-10 20:51:18 status installed libqt4-xmlpatterns:i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4
/var/log/dpkg.log.5.gz:2014-05-10 20:51:18 status installed libjpeg8:i386 8c-2ubuntu8
/var/log/dpkg.log.5.gz:2014-05-10 20:51:18 status installed libjbig0:i386 2.0-2ubuntu4.1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:18 status installed libtiff5:i386 4.0.3-7ubuntu0.1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:19 status installed libxi6:i386 2:1.7.1.901-1ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:19 status installed libxrender1:i386 1:0.9.8-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:19 status installed libqt4-sql-mysql:i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4
/var/log/dpkg.log.5.gz:2014-05-10 20:51:19 status installed libxslt1.1:i386 1.1.28-2build1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:19 status installed libxss1:i386 1:1.2.2-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:19 status installed libxv1:i386 2:1.0.10-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:19 status installed libtxc-dxtn-s2tc0:i386 0~git20131104-1.1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:19 status installed libqt4-dbus:i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4
/var/log/dpkg.log.5.gz:2014-05-10 20:51:19 status installed libqt4-declarative:i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4
/var/log/dpkg.log.5.gz:2014-05-10 20:51:19 status installed libqtgui4:i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4
/var/log/dpkg.log.5.gz:2014-05-10 20:51:19 status installed libqt4-opengl:i386 4:4.8.5+git192-g085f851+dfsg-2ubuntu4
/var/log/dpkg.log.5.gz:2014-05-10 20:51:19 status installed libqtwebkit4:i386 2.3.2-0ubuntu7
/var/log/dpkg.log.5.gz:2014-05-10 20:51:19 status installed libc-bin:amd64 2.19-0ubuntu6
/var/log/dpkg.log.5.gz:2014-05-10 20:51:21 status installed hicolor-icon-theme:all 0.13-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:21 status installed bamfdaemon:amd64 0.5.1+14.04.20140409-0ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:21 status installed skype:i386 4.2.0.13-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:21 status installed desktop-file-utils:amd64 0.22-1ubuntu1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:21 status installed gnome-menus:amd64 3.10.1-0ubuntu2
/var/log/dpkg.log.5.gz:2014-05-10 20:51:22 status installed mime-support:all 3.54ubuntu1
```

Best regards,
Jasper

---

### Post by matt_symes on 2014-10-05
Hi

> /var/log/dpkg.log.5.gz:2014-05-10 20:51:21 status installed skype:i386 4.2.0.13-1

I think skype maybe the problem and the reason why the i386 libaries are being pulled in. Have you had an update to skype in the last couple of days ?

If you can post the output of this command so we can check.

```
zgrep skype /var/log/dpkg.log*
```

> Translation: libxslt1.1 is already the newest version, so nothing was updated.

Hmm. Alright. A couple more commands to run, post the output back here, and then we should be looking at a solution.

```
apt-cache policy libxslt1.1:{i386,amd64}
```

```
dpkg -l libxslt1.1:{i386,amd64}
```

Kind regards

---

### Post by Jasper_Haller on 2014-10-06
I don't think I've had an update to skype recently. Here's the output from the *zgrep* command.

```
/var/log/dpkg.log.5.gz:2014-05-10 20:51:20 install skype:i386 <keine> 4.2.0.13-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:20 status half-installed skype:i386 4.2.0.13-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:20 status half-installed skype:i386 4.2.0.13-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:20 status half-installed skype:i386 4.2.0.13-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:20 status half-installed skype:i386 4.2.0.13-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:21 status unpacked skype:i386 4.2.0.13-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:21 status unpacked skype:i386 4.2.0.13-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:21 configure skype:i386 4.2.0.13-1 4.2.0.13-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:21 status unpacked skype:i386 4.2.0.13-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:21 status unpacked skype:i386 4.2.0.13-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:21 status half-configured skype:i386 4.2.0.13-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:21 status triggers-awaited skype:i386 4.2.0.13-1
/var/log/dpkg.log.5.gz:2014-05-10 20:51:21 status installed skype:i386 4.2.0.13-1
```

As for the other two commands, here's the output to *apt-cache *(apologies for the German mixed in, but it should be understandable, right?):

```
libxslt1.1:i386:
  Installiert:           1.1.28-2build1
  Installationskandidat: 1.1.28-2build1
  Versionstabelle:
 *** 1.1.28-2build1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main i386 Packages
        100 /var/lib/dpkg/status
libxslt1.1:
  Installiert:           1.1.28-2build1
  Installationskandidat: 1.1.28-2build1
  Versionstabelle:
 *** 1.1.28-2build1 0
        500 http://de.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
        100 /var/lib/dpkg/status
```

And here's the output to *dpkg*:

```
Gewünscht=Unbekannt/Installieren/R=Entfernen/P=Vollständig Löschen/Halten
| Status=Nicht/Installiert/Config/U=Entpackt/halb konFiguriert/
         Halb installiert/Trigger erWartet/Trigger anhängig
|/ Fehler?=(kein)/R=Neuinstallation notwendig (Status, Fehler: GROSS=schlecht)
||/ Name                                          Version                     Architektur                 Beschreibung
+++-=============================================-===========================-===========================-===============================================================================================
ii  libxslt1.1:amd64                              1.1.28-2build1              amd64                       XSLT 1.0 processing library - runtime library
ii  libxslt1.1:i386                               1.1.28-2build1              i386                        XSLT 1.0 processing library - runtime library
```

Cheers,
Jasper

---

### Post by matt_symes on 2014-10-06
Hi

According to apt and dpkg both versions of the libraries are installed however the locate command only seemed to find one version of it; the i386 version. 

This seems odd and i suspect i'm missing something really silly here.

Another command to run.

```
dpkg -L libxslt1.1:{i386,amd64}
```

This will list all the files installed by both packages. It's not a huge list so if you could post it back here.

After that if you could copy and paste this entire command block into a terminal, hit the enter key, and post back the results.
```

cd && \
dpkg -L libxslt1.1:amd64 >tmp.out && \
cat tmp.out |  while read "f"; do file "$f"; done; \
rm tmp.out
```

**EDIT:**

No need for the temporary file. Just run this

```
while read f; do file "$f"; done < <(dpkg -L libxslt1.1:amd64)
```

Kind regards

---

### Post by Jasper_Haller on 2014-10-06
This seems very strange indeed. Here's the output from the first command you posted:

```
/.
/usr
/usr/lib
/usr/lib/i386-linux-gnu
/usr/lib/i386-linux-gnu/libexslt.so.0.8.17
/usr/lib/i386-linux-gnu/libxslt.so.1.1.28
/usr/share
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/libxslt1.1
/usr/share/doc
/usr/share/doc/libxslt1.1
/usr/share/doc/libxslt1.1/README
/usr/share/doc/libxslt1.1/TODO.Debian
/usr/share/doc/libxslt1.1/README.Debian
/usr/share/doc/libxslt1.1/TODO
/usr/share/doc/libxslt1.1/copyright
/usr/share/doc/libxslt1.1/FEATURES.gz
/usr/share/doc/libxslt1.1/NEWS.gz
/usr/share/doc/libxslt1.1/AUTHORS
/usr/share/doc/libxslt1.1/changelog.Debian.gz
/usr/lib/i386-linux-gnu/libexslt.so.0
/usr/lib/i386-linux-gnu/libxslt.so.1

/.
/usr
/usr/lib
/usr/lib/x86_64-linux-gnu
/usr/lib/x86_64-linux-gnu/libxslt.so.1.1.28
/usr/lib/x86_64-linux-gnu/libexslt.so.0.8.17
/usr/share
/usr/share/lintian
/usr/share/lintian/overrides
/usr/share/lintian/overrides/libxslt1.1
/usr/share/doc
/usr/share/doc/libxslt1.1
/usr/share/doc/libxslt1.1/README
/usr/share/doc/libxslt1.1/FEATURES.gz
/usr/share/doc/libxslt1.1/TODO
/usr/share/doc/libxslt1.1/NEWS.gz
/usr/share/doc/libxslt1.1/README.Debian
/usr/share/doc/libxslt1.1/copyright
/usr/share/doc/libxslt1.1/AUTHORS
/usr/share/doc/libxslt1.1/changelog.Debian.gz
/usr/share/doc/libxslt1.1/TODO.Debian
/usr/lib/x86_64-linux-gnu/libexslt.so.0
/usr/lib/x86_64-linux-gnu/libxslt.so.1
```

As for the block of code, I get an error message: the file or directory dpkg.output cannot be found.

---

### Post by matt_symes on 2014-10-06
Hi

I have edited my last post. It was a copy and paste error on my part.

If you could run the last command from my previous post again and post the output back here.

Kind regards

---

### Post by Jasper_Haller on 2014-10-06
Gotcha. Here's the output:

```
/.: directory 
/usr: directory 
/usr/lib: directory 
/usr/lib/x86_64-linux-gnu: directory 
/usr/lib/x86_64-linux-gnu/libxslt.so.1.1.28: ERROR: cannot open `/usr/lib/x86_64-linux-gnu/libxslt.so.1.1.28' (No such file or directory)
/usr/lib/x86_64-linux-gnu/libexslt.so.0.8.17: ERROR: cannot open `/usr/lib/x86_64-linux-gnu/libexslt.so.0.8.17' (No such file or directory)
/usr/share: directory 
/usr/share/lintian: directory 
/usr/share/lintian/overrides: directory 
/usr/share/lintian/overrides/libxslt1.1: ASCII text
/usr/share/doc: directory 
/usr/share/doc/libxslt1.1: directory 
/usr/share/doc/libxslt1.1/README: ASCII text
/usr/share/doc/libxslt1.1/FEATURES.gz: gzip compressed data, from Unix, max compression
/usr/share/doc/libxslt1.1/TODO: ASCII text
/usr/share/doc/libxslt1.1/NEWS.gz: gzip compressed data, from Unix, max compression
/usr/share/doc/libxslt1.1/README.Debian: ASCII text
/usr/share/doc/libxslt1.1/copyright: UTF-8 Unicode text
/usr/share/doc/libxslt1.1/AUTHORS: UTF-8 Unicode text
/usr/share/doc/libxslt1.1/changelog.Debian.gz: gzip compressed data, from Unix, max compression
/usr/share/doc/libxslt1.1/TODO.Debian: ASCII text
/usr/lib/x86_64-linux-gnu/libexslt.so.0: ERROR: cannot open `/usr/lib/x86_64-linux-gnu/libexslt.so.0' (No such file or directory)
/usr/lib/x86_64-linux-gnu/libxslt.so.1: ERROR: cannot open `/usr/lib/x86_64-linux-gnu/libxslt.so.1' (No such file or directory)
```

---

### Post by matt_symes on 2014-10-06
Hi

> **Jasper_Haller said:**
> 
/usr/lib/x86_64-linux-gnu/libxslt.so.1.1.28: ERROR: cannot open `/usr/lib/x86_64-linux-gnu/libxslt.so.1.1.28' (No such file or directory)
/usr/lib/x86_64-linux-gnu/libexslt.so.0.8.17: ERROR: cannot open `/usr/lib/x86_64-linux-gnu/libexslt.so.0.8.17' (No such file or directory)

......

/usr/lib/x86_64-linux-gnu/libexslt.so.0: ERROR: cannot open `/usr/lib/x86_64-linux-gnu/libexslt.so.0' (No such file or directory)
/usr/lib/x86_64-linux-gnu/libxslt.so.1: ERROR: cannot open `/usr/lib/x86_64-linux-gnu/libxslt.so.1' (No such file or directory)

Well that's the problem !

Let's try reinstalling the library.

From the terminal

```
sudo apt-get install --reinstall libxslt1.1:amd64
```

Post back any errors from the above command.

If you could then run the previous command and post the output back here again. 

Kind regards

---

### Post by Jasper_Haller on 2014-10-06
Hooray! LibreOffice works! Thank you, thank you, thank you. This took a lot of patience on your part, and I really do appreciate it.

In case you're curious, the output from the command block now looks like this:

```
/.: directory 
/usr: directory 
/usr/lib: directory 
/usr/lib/x86_64-linux-gnu: directory 
/usr/lib/x86_64-linux-gnu/libxslt.so.1.1.28: ELF 64-bit LSB  shared object, x86-64, version 1 (SYSV), dynamically linked, BuildID[sha1]=a5a30291c8cd746b0014ce801eae98a4e8c9c7fb, stripped
/usr/lib/x86_64-linux-gnu/libexslt.so.0.8.17: ELF 64-bit LSB  shared object, x86-64, version 1 (SYSV), dynamically linked, BuildID[sha1]=d9345672487e4b051baf95ad9de3fa9ac2dd5a68, stripped
/usr/share: directory 
/usr/share/lintian: directory 
/usr/share/lintian/overrides: directory 
/usr/share/lintian/overrides/libxslt1.1: ASCII text
/usr/share/doc: directory 
/usr/share/doc/libxslt1.1: directory 
/usr/share/doc/libxslt1.1/README: ASCII text
/usr/share/doc/libxslt1.1/FEATURES.gz: gzip compressed data, from Unix, max compression
/usr/share/doc/libxslt1.1/TODO: ASCII text
/usr/share/doc/libxslt1.1/NEWS.gz: gzip compressed data, from Unix, max compression
/usr/share/doc/libxslt1.1/README.Debian: ASCII text
/usr/share/doc/libxslt1.1/copyright: UTF-8 Unicode text
/usr/share/doc/libxslt1.1/AUTHORS: UTF-8 Unicode text
/usr/share/doc/libxslt1.1/changelog.Debian.gz: gzip compressed data, from Unix, max compression
/usr/share/doc/libxslt1.1/TODO.Debian: ASCII text
/usr/lib/x86_64-linux-gnu/libexslt.so.0: symbolic link to `libexslt.so.0.8.17' 
/usr/lib/x86_64-linux-gnu/libxslt.so.1: symbolic link to `libxslt.so.1.1.28' 
```

Cheers,
Jasper

---

### Post by matt_symes on 2014-10-06
Hi

Excellent. That fixed it.

I'm not sure why it happened by i still think the original situation may have been Skypes installation as that was when the i386 version of the library was installed. 

Maybe the trigger to remove the amd64 version was a recent update. 

However i could be wrong here and without spending more time going through your system we will not know the reason why.

We have not got to the root cause of the problem but you do have a fix for it if it happens again. 

If you are happy with that then so am i :)

Kind regards

---

