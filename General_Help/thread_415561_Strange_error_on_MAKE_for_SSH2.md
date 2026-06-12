---
title: "Strange error on MAKE for SSH2"
date: 2007-04-20
forum: General Help
---

### Post by lynxus on 2007-04-20
Hi guys, I get this error:
Can anyone help ?


root@broken-trumpet:/home/gsmart/Downloads/ssh-3.2.9.1# make install
(test -n "" && cd "/exe" && make install) || true
(cd apps/ssh && make install)
make[1]: Entering directory `/home/gsmart/Downloads/ssh-3.2.9.1/apps/ssh'
Making install in lib
make[2]: Entering directory `/home/gsmart/Downloads/ssh-3.2.9.1/apps/ssh/lib'
Making install in sshproto
make[3]: Entering directory `/home/gsmart/Downloads/ssh-3.2.9.1/apps/ssh/lib/sshproto'
Making install in tests
make[4]: Entering directory `/home/gsmart/Downloads/ssh-3.2.9.1/apps/ssh/lib/sshproto/tests'
make[5]: Entering directory `/home/gsmart/Downloads/ssh-3.2.9.1/apps/ssh/lib/sshproto/tests'
make[5]: Nothing to be done for `install-exec-am'.
make[5]: Nothing to be done for `install-data-am'.
make[5]: Leaving directory `/home/gsmart/Downloads/ssh-3.2.9.1/apps/ssh/lib/sshproto/tests'
make[4]: Leaving directory `/home/gsmart/Downloads/ssh-3.2.9.1/apps/ssh/lib/sshproto/tests'
make[4]: Entering directory `/home/gsmart/Downloads/ssh-3.2.9.1/apps/ssh/lib/sshproto'
gcc -DHAVE_CONFIG_H -I. -I. -I../../../.. -I../../../../include -I../../../../apps/ssh/lib/sshkeyutil     -D_GNU_SOURCE -g -O2 -Wall -Wno-unknown-pragmas -D_LARGEFILE_SOURCE -D_FILE_OFFSET_BITS=64 -c ssh2compat.c
ssh2compat.c:14:25: error: sshincludes.h: No such file or directory
In file included from ssh2compat.c:15:
ssh2compat.h:17:22: error: sshcrypt.h: No such file or directory
In file included from ssh2compat.c:15:
ssh2compat.h:21: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ssh_compat_rsa_public_key_change_scheme’
ssh2compat.h:26: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ssh_compat_rsa_private_key_change_scheme’
ssh2compat.h:30: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ssh_compat_is_rsa_public_key’
ssh2compat.c:21: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ssh_compat_rsa_public_key_change_scheme’
ssh2compat.c:70: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ssh_compat_rsa_private_key_change_scheme’
ssh2compat.c:116: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ssh_compat_is_rsa_public_key’
make[4]: *** [ssh2compat.o] Error 1
make[4]: Leaving directory `/home/gsmart/Downloads/ssh-3.2.9.1/apps/ssh/lib/sshproto'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/home/gsmart/Downloads/ssh-3.2.9.1/apps/ssh/lib/sshproto'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/gsmart/Downloads/ssh-3.2.9.1/apps/ssh/lib'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/gsmart/Downloads/ssh-3.2.9.1/apps/ssh'
make: *** [kludge-install-ssh] Error 2
root@broken-trumpet:/home/gsmart/Downloads/ssh-3.2.9.1#

---

