---
title: "linux-image-generic-pae crippling Update manager"
date: 2013-07-13
forum: General Help
---

### Post by aextance on 2013-07-13
When running updates in Ubuntu 12.04, Update Manager gives the following error: 

 The following packages have unmet dependencies:

linux-generic-pae: Depends: linux-image-generic-pae (= 3.2.0.48.58) but 3.2.0.49.59 is installed
                   Depends: linux-headers-generic-pae (= 3.2.0.48.58) but 3.2.0.48.58 is installed
linux-headers-generic-pae: Depends: linux-headers-3.2.0-48-generic-pae but it is not installed

It advises me to disable third party repositories – which I have – and then run apt-get install -f in terminal

When I do that I get the following error messages:

dpkg: warning: files list file for package `linux-headers-3.2.0-49-generic-pae' missing, assuming package has no files currently installed.
(Reading database ... 678065 files and directories currently installed.)
Unpacking linux-headers-3.2.0-49 (from .../linux-headers-3.2.0-49_3.2.0-49.75_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-49_3.2.0-49.75_all.deb (--unpack):
 unable to create `/usr/src/linux-headers-3.2.0-49/arch/m32r/include/asm/irqflags.h.dpkg-new' (while processing `./usr/src/linux-headers-3.2.0-49/arch/m32r/include/asm/irqflags.h'): No space left on device
No apport report written because MaxReports has already been reached
                                                                    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to replace linux-headers-3.2.0-49-generic-pae 3.2.0-49.75 (using .../linux-headers-3.2.0-49-generic-pae_3.2.0-49.75_i386.deb) ...
Unpacking replacement linux-headers-3.2.0-49-generic-pae ...
dpkg: error processing /var/cache/apt/archives/linux-headers-3.2.0-49-generic-pae_3.2.0-49.75_i386.deb (--unpack):
 error creating directory `./usr/src/linux-headers-3.2.0-49-generic-pae/include/config/cgroup/mem': No space left on device
No apport report written because MaxReports has already been reached
                                                                    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.2.0-49_3.2.0-49.75_all.deb
 /var/cache/apt/archives/linux-headers-3.2.0-49-generic-pae_3.2.0-49.75_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

This tells me I have no space left on my device, but I have 1.8 GB, which should be enough for this update, which it says is 67.6 MB. This is the output of df -h

Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6        11G  8.2G  1.8G  83% /
udev           1000M  4.0K 1000M   1% /dev
tmpfs           403M  808K  402M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none           1007M  152K 1007M   1% /run/shm
/dev/sdb1       150G   71G   79G  48% /media/New Volume

The suggested solutions I've seen include removing old kernel headers, but when I try and do this from terminal it tells me I need to run apt-get install -f before I can do anything else, which returns the "No space left on device" error again. The same thing happens when I try to install the kernel headers package manager originally said are missing from terminal. 

Ubuntu Software Centre similarly can't do anything until this problem is fixed. I don't have Synaptic installed, and can't install it for the same reason. 

I have also tried this solution, which suggests manually changing the dpkg/status file, but it doesn't achieve anything:

[http://ubuntuforums.org/showthread.php?t=859901](http://ubuntuforums.org/showthread.php?t=859901)

All I want to do is update my system, and I've spent hours trying to do it. Can someone please help?

---

### Post by TheFu on 2013-07-13
There are 2 types of " No space left on device" errors.  Out of sectors and out of inodes.  If you run 
**df -i**, I think you'll discover you are out of inodes on /.  I run into this issue all the time with smaller (6G and less) file systems. Seems the default i-node allocation method doesn't allocate enough when lots and lots of small files - like ruby, python, php and perl developers have.

How do you fix it?  The easiest way is to get a larger HDD and mirror everything over. That used to be trivial when all HDDs were 512b sectors. Now with a mix of 512b and 4K sector sizes, that isn't a good idea - terrible HDD performance can result.  The idea is the same, but the method is more complex.

Anyway, let's verify that i-nodes is truly the issue first.  **df -i**

---

### Post by aextance on 2013-07-14
Yes, that's the problem. Here's the output of df -i

Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda6        700384 700185      199  100% /
udev             215757    536   215221    1% /dev
tmpfs            219410    453   218957    1% /run
none             219410      3   219407    1% /run/lock
none             219410      6   219404    1% /run/shm
/dev/sdb1      82682204  86275 82595929    1% /media/New Volume
/dev/sdc1      43689252  86212 43603040    1% /media/Spare

I'll have a look around and see how to fix this, but if I haven't posted anything else here I'll welcome further advice. 

The support people like you give is to me the best thing about Ubuntu - so thanks so much!

---

### Post by aextance on 2013-07-14
So I've run a command to check the number of inodes taken up on my hard drives. I keep all my work files on an external hard drive ./media, which I guess isn't relevant to this problem. 

I'm not sure which I can remove safely. As I mention above, I seem to be stuck when it comes to removing linux-headers files, etc. 

Here's the list of top space hoggersL

10 ./usr/share/icons/Humanity/status/22
211 ./boot/grub
212 ./usr/lib/grub/i386-pc
212 ./usr/share/lintian/overrides
212 ./usr/share/perl/5.14.2/unicore/lib/Blk
214 ./media/Spare/Writing/DLHE/FusionCharts_Evaluation/Contents/AttDesc/Images
214 ./usr/share/gnome/help-langpack/evolution/en_GB
216 ./proc
217 ./dev
224 ./usr/sbin
225 ./usr/src/linux-headers-3.2.0-23/arch/m68k/include/asm
225 ./usr/src/linux-headers-3.2.0-24/arch/m68k/include/asm
225 ./usr/src/linux-headers-3.2.0-25/arch/m68k/include/asm
225 ./usr/src/linux-headers-3.2.0-26/arch/m68k/include/asm
225 ./usr/src/linux-headers-3.2.0-27/arch/m68k/include/asm
225 ./usr/src/linux-headers-3.2.0-29/arch/m68k/include/asm
225 ./usr/src/linux-headers-3.2.0-30/arch/m68k/include/asm
225 ./usr/src/linux-headers-3.2.0-31/arch/m68k/include/asm
225 ./usr/src/linux-headers-3.2.0-32/arch/m68k/include/asm
225 ./usr/src/linux-headers-3.2.0-33/arch/m68k/include/asm
225 ./usr/src/linux-headers-3.2.0-35/arch/m68k/include/asm
225 ./usr/src/linux-headers-3.2.0-36/arch/m68k/include/asm
225 ./usr/src/linux-headers-3.2.0-37/arch/m68k/include/asm
225 ./usr/src/linux-headers-3.2.0-38/arch/m68k/include/asm
225 ./usr/src/linux-headers-3.2.0-39/arch/m68k/include/asm
225 ./usr/src/linux-headers-3.2.0-40/arch/m68k/include/asm
225 ./usr/src/linux-headers-3.2.0-41/arch/m68k/include/asm
225 ./usr/src/linux-headers-3.2.0-43/arch/m68k/include/asm
225 ./usr/src/linux-headers-3.2.0-44/arch/m68k/include/asm
225 ./usr/src/linux-headers-3.2.0-45/arch/m68k/include/asm
225 ./usr/src/linux-headers-3.2.0-48/arch/m68k/include/asm
233 etc
233 etc
233 ./etc
234 ./usr/lib/python2.7/dist-packages
234 ./usr/share/i18n/charmaps
236 ./run/udev/data
236 ./usr/share/apport/package-hooks
237 ./usr/share/icons/Humanity/status/24
237 ./usr/share/icons/ubuntu-mono-dark/status/24
237 ./usr/share/icons/ubuntu-mono-light/status/24
240 ./usr/share/icons/Humanity/apps/22
242 ./usr/lib/python2.7/dist-packages/twisted/test
242 ./usr/lib/python2.7/encodings
242 ./usr/share/icons/ubuntu-mono-dark/status/16
242 ./usr/share/icons/ubuntu-mono-light/status/16
243 ./usr/share/icons/ubuntu-mono-dark/status/22
243 ./usr/share/icons/ubuntu-mono-light/status/22
243 ./usr/share/media-player-info
246 ./usr/lib/i386-linux-gnu/gstreamer-0.10
251 ./usr/lib/i386-linux-gnu/sane
253 ./usr/share/man/man5
255 ./usr/share/icons/Humanity/status/16
256 ./usr/lib/i386-linux-gnu/gconv
258 ./usr/share/gimp/2.0/help/en/images/toolbox
258 ./usr/src/linux-headers-3.2.0-23/arch/mips/include/asm
258 ./usr/src/linux-headers-3.2.0-24/arch/mips/include/asm
258 ./usr/src/linux-headers-3.2.0-25/arch/mips/include/asm
258 ./usr/src/linux-headers-3.2.0-26/arch/mips/include/asm
258 ./usr/src/linux-headers-3.2.0-27/arch/mips/include/asm
258 ./usr/src/linux-headers-3.2.0-29/arch/mips/include/asm
258 ./usr/src/linux-headers-3.2.0-30/arch/mips/include/asm
258 ./usr/src/linux-headers-3.2.0-31/arch/mips/include/asm
258 ./usr/src/linux-headers-3.2.0-32/arch/mips/include/asm
258 ./usr/src/linux-headers-3.2.0-33/arch/mips/include/asm
258 ./usr/src/linux-headers-3.2.0-35/arch/mips/include/asm
258 ./usr/src/linux-headers-3.2.0-36/arch/mips/include/asm
258 ./usr/src/linux-headers-3.2.0-37/arch/mips/include/asm
258 ./usr/src/linux-headers-3.2.0-38/arch/mips/include/asm
258 ./usr/src/linux-headers-3.2.0-39/arch/mips/include/asm
258 ./usr/src/linux-headers-3.2.0-40/arch/mips/include/asm
258 ./usr/src/linux-headers-3.2.0-41/arch/mips/include/asm
258 ./usr/src/linux-headers-3.2.0-43/arch/mips/include/asm
258 ./usr/src/linux-headers-3.2.0-44/arch/mips/include/asm
258 ./usr/src/linux-headers-3.2.0-45/arch/mips/include/asm
258 ./usr/src/linux-headers-3.2.0-48/arch/mips/include/asm
261 ./var/lib/dhcp
262 ./sys/kernel/slab
266 ./usr/share/help-langpack/en_AU/ubuntu-help
266 ./usr/share/help-langpack/en_CA/ubuntu-help
266 ./usr/share/help-langpack/en_GB/ubuntu-help
267 ./usr/share/help/ar/ubuntu-help
267 ./usr/share/help/ast/ubuntu-help
267 ./usr/share/help/az/ubuntu-help
267 ./usr/share/help/bs/ubuntu-help
267 ./usr/share/help/ca/ubuntu-help
267 ./usr/share/help/cs/ubuntu-help
267 ./usr/share/help/C/ubuntu-help
267 ./usr/share/help/da/ubuntu-help
267 ./usr/share/help/de/ubuntu-help
267 ./usr/share/help/el/ubuntu-help
267 ./usr/share/help/en_AU/ubuntu-help
267 ./usr/share/help/en_CA/ubuntu-help
267 ./usr/share/help/en_GB/ubuntu-help
267 ./usr/share/help/es/ubuntu-help
267 ./usr/share/help/fi/ubuntu-help
267 ./usr/share/help/fo/ubuntu-help
267 ./usr/share/help/fr/ubuntu-help
267 ./usr/share/help/gl/ubuntu-help
267 ./usr/share/help/hi/ubuntu-help
267 ./usr/share/help/hr/ubuntu-help
267 ./usr/share/help/hu/ubuntu-help
267 ./usr/share/help/id/ubuntu-help
267 ./usr/share/help/it/ubuntu-help
267 ./usr/share/help/ja/ubuntu-help
267 ./usr/share/help/kk/ubuntu-help
267 ./usr/share/help/kn/ubuntu-help
267 ./usr/share/help/ko/ubuntu-help
267 ./usr/share/help/lt/ubuntu-help
267 ./usr/share/help/lv/ubuntu-help
267 ./usr/share/help/mg/ubuntu-help
267 ./usr/share/help/ms/ubuntu-help
267 ./usr/share/help/my/ubuntu-help
267 ./usr/share/help/nb/ubuntu-help
267 ./usr/share/help/nl/ubuntu-help
267 ./usr/share/help/oc/ubuntu-help
267 ./usr/share/help/pl/ubuntu-help
267 ./usr/share/help/pt_BR/ubuntu-help
267 ./usr/share/help/pt/ubuntu-help
267 ./usr/share/help/ru/ubuntu-help
267 ./usr/share/help/sk/ubuntu-help
267 ./usr/share/help/sl/ubuntu-help
267 ./usr/share/help/sq/ubuntu-help
267 ./usr/share/help/sr/ubuntu-help
267 ./usr/share/help/sv/ubuntu-help
267 ./usr/share/help/ta/ubuntu-help
267 ./usr/share/help/te/ubuntu-help
267 ./usr/share/help/tr/ubuntu-help
267 ./usr/share/help/ug/ubuntu-help
267 ./usr/share/help/uk/ubuntu-help
267 ./usr/share/help/uz/ubuntu-help
267 ./usr/share/help/zh_CN/ubuntu-help
267 ./usr/share/help/zh_TW/ubuntu-help
268 ./usr/share/spotify/theme/default
271 ./etc/brltty
276 ./media/Spare/Writing/Blog/Multimedia2_files
276 ./usr/lib/libreoffice/program
277 ./media/Spare/Writing/Blog/Multimedia_files
282 ./usr/share/help/ca/gnome-help
282 ./usr/share/help/C/gnome-help
282 ./usr/share/help/de/gnome-help
282 ./usr/share/help/el/gnome-help
282 ./usr/share/help/es/gnome-help
282 ./usr/share/help/fi/gnome-help
282 ./usr/share/help/fr/gnome-help
282 ./usr/share/help/gl/gnome-help
282 ./usr/share/help/hi/gnome-help
282 ./usr/share/help/hu/gnome-help
282 ./usr/share/help/id/gnome-help
282 ./usr/share/help/it/gnome-help
282 ./usr/share/help/ja/gnome-help
282 ./usr/share/help/lv/gnome-help
282 ./usr/share/help/nl/gnome-help
282 ./usr/share/help/pa/gnome-help
282 ./usr/share/help/pt_BR/gnome-help
282 ./usr/share/help/ru/gnome-help
282 ./usr/share/help/sl/gnome-help
282 ./usr/share/help/sr/gnome-help
282 ./usr/share/help/sr@latin/gnome-help
282 ./usr/share/help/sv/gnome-help
282 ./usr/share/help/te/gnome-help
282 ./usr/share/help/vi/gnome-help
282 ./usr/share/icons/Humanity/actions/22
282 ./usr/share/icons/Humanity/actions/48
287 ./media/Spare/Writing/Blog/2011
289 ./usr/share
290 ./usr/src/linux-headers-3.2.0-23/arch/sparc/include/asm
290 ./usr/src/linux-headers-3.2.0-24/arch/sparc/include/asm
290 ./usr/src/linux-headers-3.2.0-25/arch/sparc/include/asm
290 ./usr/src/linux-headers-3.2.0-26/arch/sparc/include/asm
290 ./usr/src/linux-headers-3.2.0-27/arch/sparc/include/asm
290 ./usr/src/linux-headers-3.2.0-29/arch/sparc/include/asm
290 ./usr/src/linux-headers-3.2.0-30/arch/sparc/include/asm
290 ./usr/src/linux-headers-3.2.0-31/arch/sparc/include/asm
290 ./usr/src/linux-headers-3.2.0-32/arch/sparc/include/asm
290 ./usr/src/linux-headers-3.2.0-33/arch/sparc/include/asm
290 ./usr/src/linux-headers-3.2.0-35/arch/sparc/include/asm
290 ./usr/src/linux-headers-3.2.0-36/arch/sparc/include/asm
290 ./usr/src/linux-headers-3.2.0-37/arch/sparc/include/asm
290 ./usr/src/linux-headers-3.2.0-38/arch/sparc/include/asm
290 ./usr/src/linux-headers-3.2.0-39/arch/sparc/include/asm
290 ./usr/src/linux-headers-3.2.0-40/arch/sparc/include/asm
290 ./usr/src/linux-headers-3.2.0-41/arch/sparc/include/asm
290 ./usr/src/linux-headers-3.2.0-43/arch/sparc/include/asm
290 ./usr/src/linux-headers-3.2.0-44/arch/sparc/include/asm
290 ./usr/src/linux-headers-3.2.0-45/arch/sparc/include/asm
290 ./usr/src/linux-headers-3.2.0-48/arch/sparc/include/asm
296 ./usr/share/icons/Humanity/actions/16
297 ./usr/src/linux-headers-3.2.0-23/arch/powerpc/include/asm
297 ./usr/src/linux-headers-3.2.0-24/arch/powerpc/include/asm
297 ./usr/src/linux-headers-3.2.0-25/arch/powerpc/include/asm
297 ./usr/src/linux-headers-3.2.0-26/arch/powerpc/include/asm
297 ./usr/src/linux-headers-3.2.0-27/arch/powerpc/include/asm
297 ./usr/src/linux-headers-3.2.0-29/arch/powerpc/include/asm
297 ./usr/src/linux-headers-3.2.0-30/arch/powerpc/include/asm
297 ./usr/src/linux-headers-3.2.0-31/arch/powerpc/include/asm
297 ./usr/src/linux-headers-3.2.0-32/arch/powerpc/include/asm
297 ./usr/src/linux-headers-3.2.0-33/arch/powerpc/include/asm
297 ./usr/src/linux-headers-3.2.0-35/arch/powerpc/include/asm
297 ./usr/src/linux-headers-3.2.0-36/arch/powerpc/include/asm
297 ./usr/src/linux-headers-3.2.0-37/arch/powerpc/include/asm
297 ./usr/src/linux-headers-3.2.0-38/arch/powerpc/include/asm
297 ./usr/src/linux-headers-3.2.0-39/arch/powerpc/include/asm
297 ./usr/src/linux-headers-3.2.0-40/arch/powerpc/include/asm
297 ./usr/src/linux-headers-3.2.0-41/arch/powerpc/include/asm
297 ./usr/src/linux-headers-3.2.0-43/arch/powerpc/include/asm
297 ./usr/src/linux-headers-3.2.0-44/arch/powerpc/include/asm
297 ./usr/src/linux-headers-3.2.0-45/arch/powerpc/include/asm
297 ./usr/src/linux-headers-3.2.0-48/arch/powerpc/include/asm
299 ./media/Spare/Writing/Blog/2012
300 ./usr/share/consolefonts
301 ./usr/share/icons/Humanity/mimes/16
312 ./usr/src/linux-headers-3.2.0-23/arch/x86/include/asm
312 ./usr/src/linux-headers-3.2.0-24/arch/x86/include/asm
312 ./usr/src/linux-headers-3.2.0-25/arch/x86/include/asm
312 ./usr/src/linux-headers-3.2.0-26/arch/x86/include/asm
312 ./usr/src/linux-headers-3.2.0-27/arch/x86/include/asm
312 ./usr/src/linux-headers-3.2.0-29/arch/x86/include/asm
312 ./usr/src/linux-headers-3.2.0-30/arch/x86/include/asm
312 ./usr/src/linux-headers-3.2.0-31/arch/x86/include/asm
312 ./usr/src/linux-headers-3.2.0-32/arch/x86/include/asm
312 ./usr/src/linux-headers-3.2.0-33/arch/x86/include/asm
312 ./usr/src/linux-headers-3.2.0-35/arch/x86/include/asm
312 ./usr/src/linux-headers-3.2.0-36/arch/x86/include/asm
312 ./usr/src/linux-headers-3.2.0-37/arch/x86/include/asm
312 ./usr/src/linux-headers-3.2.0-38/arch/x86/include/asm
312 ./usr/src/linux-headers-3.2.0-39/arch/x86/include/asm
312 ./usr/src/linux-headers-3.2.0-40/arch/x86/include/asm
312 ./usr/src/linux-headers-3.2.0-41/arch/x86/include/asm
312 ./usr/src/linux-headers-3.2.0-43/arch/x86/include/asm
312 ./usr/src/linux-headers-3.2.0-44/arch/x86/include/asm
312 ./usr/src/linux-headers-3.2.0-45/arch/x86/include/asm
312 ./usr/src/linux-headers-3.2.0-48/arch/x86/include/asm
313 ./usr/share/icons/Humanity/actions/24
315 ./usr/share/i18n/locales
329 ./usr/share/icons/Humanity/apps/48
345 ./usr/share/icons/Humanity/mimes/24
346 ./usr/share/icons/Humanity/mimes/22
366 ./usr/share/gimp/2.0/help/en/images/filters/examples
370 ./usr/share/icons/Humanity/mimes/48
377 ./usr/share/icons/Humanity/apps/24
378 ./usr/share/mime/application
386 ./media/Spare/games/syndicate/Syndicate/DATA
390 ./usr/share/locale-langpack/en_AU/LC_MESSAGES
390 ./usr/share/locale-langpack/en_GB/LC_MESSAGES
393 ./usr/include/linux
414 ./usr/share/fonts/X11/misc
425 ./usr/share/man/man2
440 ./usr/lib/python2.7
464 ./media/Spare/Writing/Blog/2010
465 ./etc/ssl/certs
517 ./usr/share/man/man8
551 ./media/Spare/games/Darklands/PICS
564 ./media/Spare/games/CM4/temp/4ACD0670-000D0C26/savegame/rgman
570 ./usr/share/gimp/2.0/help/en
777 ./var/cache/apt/archives
815 ./usr/lib
849 ./media/Spare/Dropbox/Photos/Family&friends/emma
865 ./usr/lib/i386-linux-gnu
1152 ./usr/src/linux-headers-3.2.0-23/include/linux
1152 ./usr/src/linux-headers-3.2.0-24/include/linux
1152 ./usr/src/linux-headers-3.2.0-25/include/linux
1152 ./usr/src/linux-headers-3.2.0-26/include/linux
1152 ./usr/src/linux-headers-3.2.0-27/include/linux
1152 ./usr/src/linux-headers-3.2.0-29/include/linux
1152 ./usr/src/linux-headers-3.2.0-30/include/linux
1152 ./usr/src/linux-headers-3.2.0-31/include/linux
1152 ./usr/src/linux-headers-3.2.0-32/include/linux
1152 ./usr/src/linux-headers-3.2.0-33/include/linux
1152 ./usr/src/linux-headers-3.2.0-35/include/linux
1152 ./usr/src/linux-headers-3.2.0-36/include/linux
1152 ./usr/src/linux-headers-3.2.0-37/include/linux
1152 ./usr/src/linux-headers-3.2.0-38/include/linux
1152 ./usr/src/linux-headers-3.2.0-39/include/linux
1152 ./usr/src/linux-headers-3.2.0-40/include/linux
1152 ./usr/src/linux-headers-3.2.0-41/include/linux
1152 ./usr/src/linux-headers-3.2.0-43/include/linux
1152 ./usr/src/linux-headers-3.2.0-44/include/linux
1152 ./usr/src/linux-headers-3.2.0-45/include/linux
1152 ./usr/src/linux-headers-3.2.0-48/include/linux
1153 ./usr/src/linux-headers-3.2.0-23-generic-pae/include/linux
1153 ./usr/src/linux-headers-3.2.0-24-generic-pae/include/linux
1153 ./usr/src/linux-headers-3.2.0-25-generic-pae/include/linux
1153 ./usr/src/linux-headers-3.2.0-26-generic-pae/include/linux
1153 ./usr/src/linux-headers-3.2.0-27-generic-pae/include/linux
1153 ./usr/src/linux-headers-3.2.0-29-generic-pae/include/linux
1153 ./usr/src/linux-headers-3.2.0-30-generic-pae/include/linux
1153 ./usr/src/linux-headers-3.2.0-31-generic-pae/include/linux
1153 ./usr/src/linux-headers-3.2.0-32-generic-pae/include/linux
1153 ./usr/src/linux-headers-3.2.0-33-generic-pae/include/linux
1153 ./usr/src/linux-headers-3.2.0-35-generic-pae/include/linux
1153 ./usr/src/linux-headers-3.2.0-36-generic-pae/include/linux
1153 ./usr/src/linux-headers-3.2.0-37-generic-pae/include/linux
1153 ./usr/src/linux-headers-3.2.0-38-generic-pae/include/linux
1153 ./usr/src/linux-headers-3.2.0-39-generic-pae/include/linux
1153 ./usr/src/linux-headers-3.2.0-40-generic-pae/include/linux
1153 ./usr/src/linux-headers-3.2.0-41-generic-pae/include/linux
1153 ./usr/src/linux-headers-3.2.0-43-generic-pae/include/linux
1153 ./usr/src/linux-headers-3.2.0-44-generic-pae/include/linux
1153 ./usr/src/linux-headers-3.2.0-45-generic-pae/include/linux
1238 ./usr/share/man/man1
1265 ./usr/src/linux-headers-3.2.0-23-generic-pae/include/config
1265 ./usr/src/linux-headers-3.2.0-24-generic-pae/include/config
1265 ./usr/src/linux-headers-3.2.0-25-generic-pae/include/config
1265 ./usr/src/linux-headers-3.2.0-26-generic-pae/include/config
1265 ./usr/src/linux-headers-3.2.0-27-generic-pae/include/config
1265 ./usr/src/linux-headers-3.2.0-29-generic-pae/include/config
1265 ./usr/src/linux-headers-3.2.0-30-generic-pae/include/config
1265 ./usr/src/linux-headers-3.2.0-31-generic-pae/include/config
1265 ./usr/src/linux-headers-3.2.0-32-generic-pae/include/config
1265 ./usr/src/linux-headers-3.2.0-33-generic-pae/include/config
1266 ./usr/src/linux-headers-3.2.0-35-generic-pae/include/config
1266 ./usr/src/linux-headers-3.2.0-36-generic-pae/include/config
1266 ./usr/src/linux-headers-3.2.0-37-generic-pae/include/config
1266 ./usr/src/linux-headers-3.2.0-38-generic-pae/include/config
1266 ./usr/src/linux-headers-3.2.0-39-generic-pae/include/config
1267 ./usr/src/linux-headers-3.2.0-40-generic-pae/include/config
1267 ./usr/src/linux-headers-3.2.0-41-generic-pae/include/config
1267 ./usr/src/linux-headers-3.2.0-43-generic-pae/include/config
1267 ./usr/src/linux-headers-3.2.0-44-generic-pae/include/config
1267 ./usr/src/linux-headers-3.2.0-45-generic-pae/include/config
1281 ./usr/bin
1560 ./usr/share/man/man3
1572 ./usr/share/doc
2211 ./usr/share/app-install/icons
2590 ./usr/share/app-install/desktop
6710 ./var/lib/dpkg/info

---

### Post by Impavidus on 2013-07-14
Uninstall some old kernel header packages```
sudo apt-get purge linux-headers-3.2.0-{{23..27},{29..33},{35..41},43,44}{,-generic-pae}
```You can probably uninstall some old kernels too.

---

### Post by aextance on 2013-07-14
Thanks, but that code won't run. This is the message I get: 

The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.48.58) but 3.2.0.49.59 is to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-48-generic-pae but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Which is where I came in!

---

### Post by TheFu on 2013-07-14
The simple answer is that you **need** more inodes/sector for the file system used.  There isn't anyway to modify that (maybe there is, but I've never heard or used it), so the best answer is to build a new file system with 3x-10x the default number of inodes.

i-nodes don't take hardly any space, so don't worry about that at all, it is just a tuning parameter set when a new file system is created using **newfs** or **mkfs** tools.  Don't let a GUI tool make it for you - that will result in the same situation you have now.

High Level Steps:
* Have good backup that you trust 100%. It needs to understand Linux permissions, ACLs, user, group, and special file stuff - not just the data contents.
* Wipe the current / file system - probably not really needed, since **mkfs** will effectively do that.
* Read and understand the man pages for **mkfs** - especially about the inode allocations.  
* Build the exact mkfs command you will use and test it.  check that the number of inodes created is 3-10x more than the current numbers.
* Restore all the files from your backup.
Be happy.

There might be a better way using **tune2fs**.  I'd google for 10 minutes on "resize inodes" before doing anything destructive. The backup that you trust step is still important. Screwing around with file systems at this level is very dangerous. Data loss is likely.

---

### Post by Bashing-om on 2013-07-14
aextance; Hi !

We have got to get you some operating head space. 
Maybe try this as the "gang" approach did not succeed. 
Removing the images and headers will free up some inodes. What results if you try and remove the linux-images and linux-headers files one at a time ?
CLI method:
From your Terminal session enter:
```

dpkg -l | grep linux-image-
dpkg -l }grep linux-headers-

``` so you KNOW what kernels are installed. Remove all but the latest(the one you are booting from) and one prior.
```

sudo apt-get --purge remove linux-image3.2.0-23-generic-pae
sudo apt-get --purge remove linux-headers3.2.0-23-generic-pae

``` for each kernel to be removed, substituting in the appropriate kernel version number.
When all done .. make sure all is cleaned up with.
```
sudo apt-get --purge autoremove
```
When you have the operating room, and all is cleaned up... will see what it takes to get the latest kernel installed.

[INDENT][INDENT][INDENT]just try'n to help
[/INDENT][/INDENT][/INDENT]

---

### Post by TheFu on 2013-07-14
> **Bashing-om said:**
> aextance; Hi !

We have got to get you some operating head space. 

@Bashing-om is 100% correct, but know that unless the system is extremely static, you will hit the inode limit again and again and again.  I tried to patch mine over and over and over, until I'd spent more time and hassle on that then re-tuning the file system would have taken in the first place.  Plus, the inodes never ran out when I had 5 hours to screw around - it always waited until I was catching a flight overseas for 3 weeks or headed to a funeral.

I had scripts running daily to watch the inodes so I'd be able to take per-emptive steps. That worked for a few months.

Certainly, getting more inode headroom will help initially, but it isn't the final solution.  Only you can decide which will work the best.

---

### Post by Bashing-om on 2013-07-14
^+10^ if this is a production machine .

---

### Post by Impavidus on 2013-07-14
> **Bashing-om said:**
> aextance; Hi !

We have got to get you some operating head space. 
Maybe try this as the "gang" approach did not succeed. 
Removing the images and headers will free up some inodes. What results if you try and remove the linux-images and linux-headers files one at a time ?
CLI method:
From your Terminal session enter:
```

dpkg -l | grep linux-image-
dpkg -l | grep linux-headers-

```...

If this doesn't work either, you may be able to delete a few thousand files from /usr/scr/linux-headers-whatever (not the latest versions) manually (use rm, don't put them in trash), run **sudo apt-get install -f** and then uninstall the packages. It should free up about 100000 inodes.

I agree the best solution is to get more inodes available.

---

### Post by aextance on 2013-07-16
Thanks for all your help everyone, but no dice so far. I've managed to free up 5158 inodes by emptying home/.thumbnails, but the IUse% is still 100.

The apt-get --purge remove gets this message:

You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-generic-pae : Depends: linux-image-generic-pae (= 3.2.0.48.58) but 3.2.0.49.59 is to be installed
 linux-headers-generic-pae : Depends: linux-headers-3.2.0-48-generic-pae but it is not going to be installed

Is that linked to these statements from the ls grep output? 

ii  linux-headers-3.2.0-48                 3.2.0-48.74                             Header files related to Linux kernel version 3.2.0
iH  linux-headers-3.2.0-49-generic-pae     3.2.0-49.75                             (no description available)
iU  linux-headers-generic-pae              3.2.0.48.58 

and 

ii  linux-image-3.2.0-48-generic-pae       3.2.0-48.74                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-49-generic-pae       3.2.0-49.75                             Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-generic-pae                3.2.0.49.59                             Generic Linux kernel image

just using rm doesn't work as I get this message

rm: cannot remove `./usr/src/linux-headers-3.2.0-23-generic-pae': Is a directory

As far as using mkfs goes I'm using Ubuntu in a dual-boot with Windows that I built on a 10-year-old desktop using a live CD. It's got a comparatively small hard drive by today's standards, though the processor was nearly top of the range at the time, and I've upgraded the RAM. I keep all my valuable data on an external hard drive that I back up onto a second drive. I seem to remember doing this so it would be easier to reinstall Ubuntu when the inevitable snafu occurred - I think it's only really Firefox bookmarks I need to backup. The reason for this rambling story is as a prelude to the question: could I build an Ubuntu partition from a live CD with an adequately high level of iNodes? 

I'm moderately techie but no expert, and got lured into Ubuntu by the "It just works" slogan when I ended up with a laptop with no operating system. It strikes me the world needs a free operating system, especially one that will keep old and simple systems running - however, perhaps inevitably Ubuntu seems much more geared towards the newest systems to me. I really like many aspects of the philosophy, and the community (ie you guys) is wonderful. But the comment about "5 hours to play around" is well made - I really resent all the hours I've had to spend fixing Ubuntu, when I want it to "just work". So I spend more and more time in my Windows partition, and have now made it my main work environment rather than Ubuntu. And now, just to update the system, I need to spend time puzzling this out? Really, isn't it just going to be simpler to reinstall? In fact, maybe I'll just ignore it - I only use Ubuntu to back up the files that Windows doesn't like these days. 

But as much as I'm getting bitter about Ubuntu, I remain incredibly grateful to guys like you. And now, if you can suggest a simple way out of this for me, then great. If not, then thanks again, anyway.

---

### Post by Bashing-om on 2013-07-16
aextance; Stubborn situation;

(Re-)installing is a means of last resort, and there are benefits for the learning curve to do so. However, all we have to do is unconfuse the operating system in respect to the linux-image to get ya back up and running.
This:
```

sudo dpkg --remove linux-generic-pae
sudo apt-get install linux-generic-pae
```
Removing linux-generic will do no harm at all. It is only a "meta-package" depending on linux-image-generic and linux-headers-generic. Those two are themselves meta-packages depending on the respective latest image/headers packages.

You can see this for yourself by issuing apt-cache show linux-generic, apt-cache show linux-image-generic and apt-cache show linux-headers-generic.

The purpose of meta-packages is to pull-in the packages on which they depend, they have no functionality at all. On the other hand removing one will not remove it's dependencies - so no danger to the system.

After having fixed the original issue you can of course install linux-generic again.

------------
Sometimes the best thing to say is nothing at all. If it is broke we fix it.

[INDENT][INDENT][INDENT]operating system of choice
[/INDENT][/INDENT][/INDENT]

---

### Post by aextance on 2013-07-16
Brilliant, thanks Bashing-om, that's fixed it. After doing that for both linux-headers-generic-pae and linux-generic-pae I could run sudo apt-get purge and get rid of all my old linux headers, and now 42% of my inodes are available again! So update-manager works smoothly, and we are now back to sulk-free Ubuntu again! Thanks for everything including putting up with my sulk earlier. 

I just registered what you said about a GUI getting me into the same problem if I were to reconfigure my partition - I'll have a look at mkfs and hopefully will be able to sort something that will stay error-free for longer. I'll say it again: people like you are my favourite thing about Ubuntu!

---

### Post by Bashing-om on 2013-07-16
aextance; Outstanding !

It is but a mater of learning the tools at our disposal. A little poking and prodding to see what this smart operating system wants.

If you maintain "house cleaning" - ubuntu does not require much - this situation should not pop up again. There is a learning curve to become knowledgeable. I rest assured I will never ever know it all, and that for sure keeps me entertained. This system is ever evolving... meeting the demands of our technological society !
And I say again -> ubuntu, the greatest operating system the world has ever known.

[INDENT][INDENT]just keep on keep'n on[/INDENT][/INDENT]

---

