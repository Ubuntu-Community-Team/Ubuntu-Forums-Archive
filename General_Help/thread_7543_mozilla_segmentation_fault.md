---
title: "mozilla segmentation fault"
date: 2004-12-08
forum: General Help
---

### Post by madamox on 2004-12-08
--Firefox 1.0
it seems to crash randomly at different times on different sites, here is my strace for it....


ioctl(3, FIONREAD, [0]) = 0
poll([{fd=3, events=POLLIN}, {fd=8, events=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN|POLLPRI}, {fd=15, events=POLLIN|POLLPRI}, {fd=16, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN}, {fd=4, events=POLLIN, revents=POLLIN}], 8, 0) = 1
read(4, "\372", 1) = 1
ioctl(3, FIONREAD, [0]) = 0
poll([{fd=3, events=POLLIN}, {fd=8, events=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN|POLLPRI}, {fd=15, events=POLLIN|POLLPRI}, {fd=16, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN}, {fd=4, events=POLLIN}], 8, 0) = 0
mmap2(NULL, 167936, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x44f31000
write(3, "5\30\4\0\260\"\200\2\266\0\0\0\21\0\21\0F\3\5\0\260\"\200"..., 116) = 116
read(3, 0xbfffd6a0, 32) = -1 EAGAIN (Resource temporarily unavailable)
select(4, [3], NULL, NULL, NULL) = 1 (in [3])
read(3, "\6\0\226\261\357\37c\1\266\0\0\0\177\0\200\2\0\0\0\0^\2"..., 32) = 32
read(3, 0xbfffd6a0, 32) = -1 EAGAIN (Resource temporarily unavailable)
select(4, [3], NULL, NULL, NULL) = 1 (in [3])
read(3, "\1\2\235\261\0\0\0\0O\0\200\2\0\0\0\0\0\0\0\0\36\0\0\0"..., 32) = 32
munmap(0x44f31000, 167936) = 0
mmap2(NULL, 167936, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x44f31000
write(3, ";\3\5\0\n\0\200\2\0\0\0\0\0\0\0\0\20\0\20\0\225\3\n\0\260"..., 1316) = 1316
read(3, 0xbfffd6a0, 32) = -1 EAGAIN (Resource temporarily unavailable)
select(4, [3], NULL, NULL, NULL) = 1 (in [3])
read(3, "\1\2\331\261\0\0\0\0O\0\200\2\0\0\0\0\0\0\0\0\36\0\0\0"..., 32) = 32
munmap(0x44f31000, 167936) = 0
write(3, "\225\3\n\0\262\"\200\2\n\0\200\2\0\6@\0\0\0\0\0\0\0012"..., 1772) = 1772
poll([{fd=3, events=POLLIN}, {fd=8, events=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN|POLLPRI}, {fd=15, events=POLLIN|POLLPRI}, {fd=16, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN}], 7, 0) = 0
ioctl(3, FIONREAD, [0]) = 0
gettimeofday({1102462476, 67123}, NULL) = 0
ioctl(3, FIONREAD, [0]) = 0
poll([{fd=3, events=POLLIN}, {fd=8, events=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN|POLLPRI}, {fd=15, events=POLLIN|POLLPRI}, {fd=16, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN}, {fd=4, events=POLLIN, revents=POLLIN}], 8, -1) = 1
gettimeofday({1102462476, 67469}, NULL) = 0
gettimeofday({1102462476, 67505}, NULL) = 0
gettimeofday({1102462476, 67626}, NULL) = 0
futex(0x81f7824, FUTEX_WAKE, 1) = 1
futex(0x81f7814, FUTEX_WAKE, 1) = 1
read(4, "\372", 1) = 1
ioctl(3, FIONREAD, [0]) = 0
poll([{fd=3, events=POLLIN, revents=POLLIN}, {fd=8, events=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN|POLLPRI}, {fd=15, events=POLLIN|POLLPRI}, {fd=16, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN}, {fd=4, events=POLLIN}], 8, -1) = 1
ioctl(3, FIONREAD, [32]) = 0
read(3, "\6\0\331\261\374\37c\1\266\0\0\0\177\0\200\2\0\0\0\0`\2"..., 32) = 32
ioctl(3, FIONREAD, [0]) = 0
gettimeofday({1102462476, 68255}, NULL) = 0
ioctl(3, FIONREAD, [0]) = 0
poll([{fd=3, events=POLLIN, revents=POLLIN}, {fd=8, events=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN|POLLPRI}, {fd=15, events=POLLIN|POLLPRI}, {fd=16, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN}, {fd=4, events=POLLIN}], 8, -1) = 1
ioctl(3, FIONREAD, [32]) = 0
read(3, "\6\0&\262\n c\1\266\0\0\0\177\0\200\2\0\0\0\0a\2V\0*\2"..., 32) = 32
ioctl(3, FIONREAD, [0]) = 0
gettimeofday({1102462476, 81905}, NULL) = 0
ioctl(3, FIONREAD, [0]) = 0
poll([{fd=3, events=POLLIN}, {fd=8, events=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN|POLLPRI}, {fd=15, events=POLLIN|POLLPRI}, {fd=16, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN}, {fd=4, events=POLLIN, revents=POLLIN}], 8, -1) = 1
gettimeofday({1102462476, 90284}, NULL) = 0
gettimeofday({1102462476, 90332}, NULL) = 0
gettimeofday({1102462476, 324416}, NULL) = 0
futex(0x81f7824, FUTEX_WAKE, 1) = 1
futex(0x81f7814, FUTEX_WAKE, 1) = 1
read(4, "\372", 1) = 1
ioctl(3, FIONREAD, [32]) = 0
read(3, "\6\0&\262\270 c\1\266\0\0\0\177\0\200\2\0\0\0\0c\2W\0,"..., 32) = 32
poll([{fd=3, events=POLLIN, revents=POLLIN}, {fd=8, events=POLLIN}, {fd=12, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN|POLLPRI}, {fd=15, events=POLLIN|POLLPRI}, {fd=16, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN}], 7, 0) = 1
ioctl(3, FIONREAD, [32]) = 0
read(3, "\6\0&\262\306 c\1\266\0\0\0\177\0\200\2\0\0\0\0d\2W\0-"..., 32) = 32
ioctl(3, FIONREAD, [32]) = 0
read(3, "\6\0&\262\323 c\1\266\0\0\0\177\0\200\2\0\0\0\0h\2[\000"..., 32) = 32
ioctl(3, FIONREAD, [32]) = 0
read(3, "\6\0&\262\340 c\1\266\0\0\0\177\0\200\2\0\0\0\0j\2[\000"..., 32) = 32
ioctl(3, FIONREAD, [32]) = 0
read(3, "\6\0&\262\356 c\1\266\0\0\0\177\0\200\2\0\0\0\0p\2a\000"..., 32) = 32
ioctl(3, FIONREAD, [0]) = 0
gettimeofday({1102462476, 325867}, NULL) = 0
write(3, "\2\3\4\0S\0\200\2\0@\0\0u\1\200\2", 16) = 16
write(5, "\372", 1) = 1
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
unlink("/home/madamox/.mozilla/firefox/default.vk5/lock") = 0
rt_sigaction(SIGSEGV, {SIG_DFL}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [SEGV], NULL, 8) = 0
tgkill(11790, 11790, SIGSEGV) = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV +++




here is my crash with epiphany... looks like pretty much the same thing to me


gettimeofday({1102474912, 624811}, NULL) = 0
lseek(40, 14336, SEEK_SET) = 14336
write(40, "\0\1\0\5\221\0\0(\0\0\0\24A\266n\237A\266a,A\271\262\211"..., 512) = 512
write(20, "\372", 1) = 1
write(3, ">\7\7\0\330:\200\2\230:\200\2\6\0\200\2\0\0\0\0\f\0\2\0"..., 636) = 63 6
ioctl(3, FIONREAD, [0]) = 0
gettimeofday({1102474912, 631222}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI }, {fd=10, events=POLLIN}, {fd=13, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN |POLLPRI}, {fd=15, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN|POLLPRI}, {fd=1 6, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}], 10, 0) = 0
ioctl(3, FIONREAD, [0]) = 0
gettimeofday({1102474912, 640039}, NULL) = 0
poll([{fd=4, events=POLLIN}, {fd=3, events=POLLIN}, {fd=8, events=POLLIN|POLLPRI }, {fd=10, events=POLLIN}, {fd=13, events=POLLIN|POLLPRI}, {fd=14, events=POLLIN |POLLPRI}, {fd=15, events=POLLIN|POLLPRI}, {fd=17, events=POLLIN|POLLPRI}, {fd=1 6, events=POLLIN|POLLPRI}, {fd=12, events=POLLIN|POLLPRI}, {fd=19, events=POLLIN , revents=POLLIN}], 11, 0) = 1
gettimeofday({1102474912, 640283}, NULL) = 0
brk(0) = 0x897c000
brk(0x899d000) = 0x899d000
gettimeofday({1102474912, 682355}, NULL) = 0
gettimeofday({1102474912, 721551}, NULL) = 0
time(NULL) = 1102474912
time(NULL) = 1102474912
time(NULL) = 1102474912
time(NULL) = 1102474912
gettimeofday({1102474912, 726967}, NULL) = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
unlink("/home/madamox/.gnome2/epiphany/mozilla/epiphany/lock") = 0
write(3, "\f\7\7\0\341:\200\2\17\0\200\2\0\0\0\0\0\0\0\0\324\1\0"..., 980) = 980
write(3, " \7\2\0\0\0\0\0", 8) = 8
write(3, "+\7\1\0", 4) = 4
read(3, "\26\275\323\334\341:\200\2\341:\200\2\0\0\0\0\0\0\0\0\324"..., 32) = 32
read(3, "\26\275\324\334\342:\200\2\342:\200\2\0\0\0\0\0\0\0\0\324"..., 32) = 32
read(3, "\23\0\326\334\342:\200\2\342:\200\2\0\274\v\10\270\20\234"..., 32) = 32
read(3, "\23:\330\334\341:\200\2\341:\200\2\0\274\v\10\270\20\234"..., 32) = 32
read(3, "\26\275\331\334\341:\200\2\341:\200\2\0\0\0\0\275\3:\0"..., 32) = 32
read(3, "\26\275\332\334\341:\200\2\341:\200\2\0\0\0\0\277\3:\0"..., 32) = 32
read(3, "\26\275\333\334\341:\200\2\341:\200\2\0\0\0\0\277\3\t\0"..., 32) = 32
read(3, "\26\275\334\334\341:\200\2\341:\200\2\0\0\0\0\277\3\35"..., 32) = 32
read(3, "\26\275\335\334\341:\200\2\341:\200\2\0\0\0\0\274\1\35"..., 32) = 32
read(3, "\26\275\343\334\341:\200\2\341:\200\2\0\0\0\0\262\1\35"..., 32) = 32
read(3, "\26\275\344\334\325:\200\2\325:\200\2\0\0\0\0\0\0\0\0\272"..., 32) = 32
read(3, "\26\275\345\334\326:\200\2\326:\200\2\0\0\0\0\0\0\0\0\272"..., 32) = 32
read(3, "\22\307\355\334\3763\200\2\3763\200\2\0\20\234\10\3763"..., 32) = 32
read(3, "\f\367\355\334\3633\200\2\262\1\35\0\324\1<\0\0\0\f@\374"..., 32) = 32
read(3, "\22\307\356\334\3773\200\2\3773\200\2\0\20\234\10\3773"..., 32) = 32
read(3, "\21\345\357\334\3773\200\2\3773\200\2\0\0\0\0\24\0\0\0"..., 32) = 32
read(3, "\21x\360\334\3763\200\2\3763\200\2\246\223\f\10\24\0\0"..., 32) = 32
read(3, "\1\2\363\334\0\0\0\0<\0\200\2\0\0\0\0\1\0\0\0\36\0\0\0"..., 32) = 32
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, chil d_tidptr=0x40eb1be8) = 15279
waitpid(15279, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0) = 15279
exit_group(1) = ?


It crashes quite often... I also get a segmentation fault crash with dvdrip, before i even get into the encoding process, if needed i can post the strace report here... i dont know if its a bug or something ive done... if it is a bug im just posting to report it... if i can fix this problem that would be great cuz it is a huge inconvenience

---

### Post by madamox on 2004-12-08
oh sorry guess i shoudve disabled smileys on that post  :oops:

---

### Post by randy on 2004-12-08
You'll want to file this as a bug if you want it to get noticed by the developers.

---

### Post by liuter2045 on 2007-05-15
Re: mozilla segmentation fault
[mapquest physics Pay Day Loans Ebay Equity Loans](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/anal-porn.html)

---

### Post by Leemur51 on 2007-05-15
> **randy said:**
> You'll want to file this as a bug if you want it to get noticed by the developers.


[magnets demonstrate chemistry bread magnets](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/anal-porn.html)

---

