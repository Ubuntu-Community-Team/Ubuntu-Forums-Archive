---
title: "Error building hello****"
date: 2017-02-15
forum: General Help
---

### Post by davinp on 2017-02-15
Here is the output from issuing the command ./configure

www@davin-Aspire-ES1-511:~/hello****$ su
Password:
root@davin-Aspire-ES1-511:/home/www/hello****# ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables...
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking for stdlib.h... (cached) yes
checking for unistd.h... (cached) yes
checking for stdlib.h... (cached) yes
checking for GNU libc compatible malloc... yes
checking for sqrt... no
configure: creating ./config.status
config.status: creating Makefile
config.status: creating doc/Makefile
config.status: creating man/Makefile
config.status: creating script/Makefile
config.status: creating src/Makefile
config.status: executing depfiles commands
root@davin-Aspire-ES1-511:/home/www/hello****#

The command "make" does nothing and the contents of the Makefile are
as follows:

root@davin-Aspire-ES1-511:/home/www/hello****# make
make: *** No targets.  Stop.
root@davin-Aspire-ES1-511:/home/www/hello****# cat Makefile
AUTOMAKE_OPTIONS = foreign
SUBDIRS = src doc man script

---

### Post by lisati on 2017-02-15
Duplicate here: [https://ubuntuforums.org/showthread.php?t=2352809](https://ubuntuforums.org/showthread.php?t=2352809)

Please don't start multiple threads for the same problem, it dilutes the community's ability to help and it can get confusing.

I've moved your other thread to the "Programming Talk" section.

---

