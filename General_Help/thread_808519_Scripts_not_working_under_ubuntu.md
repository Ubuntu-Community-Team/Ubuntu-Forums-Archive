---
title: "Scripts not working under ubuntu"
date: 2008-05-26
forum: General Help
---

### Post by spamalam on 2008-05-26
Can anyone help out in fixing the following scripts?

First up i have a start script I'm trying to run:
```
$ ./startAdmin.sh
./startAdmin.sh: 7: [[: not found
./common.sh: 23: [[: not found
shift: 23: can't shift that many

```

Line 1-7 of startAdmin.sh:
```

#!/bin/sh

if [[ -n ${SCRIPT_DEBUG} ]]
then
  set -xv
  typeset -ft $(typeset +f)
fi

```

Line 23 of common.sh lands slap bang in the middle of:
```

if [[ -z $1 ]] ; then
   export SERVER_NAME=NAME

   export SSL_OPTIONS="-Dproperties=here \
-Dproperties=here \
-Dproperties=here"
else
   shift 1
fi

```

Very strange, do if statements not work with [[ and how come?  Syntaxicly they work fine on some other varients of nix i have. My shell is ksh and the shell scripts define !#/bin/sh..

---

### Post by cdtech on 2008-05-26
What editor did you use to create the script?

---

### Post by Monicker on 2008-05-26
Is this 8.04?  If so, could the issues be due to the fact that dash is the default shell? /bin/sh is a symlink to /bin/dash in Hardy.

---

### Post by spamalam on 2008-05-26
> What editor did you use to create the script?

Generated in python and then i run dos2unix on them to get rid of the windows characters.

Details on the distro:
$ uname -a
Linux jake 2.6.22-14-generic #1 SMP Fri Feb 1 04:59:50 UTC 2008 i686 GNU/Linux

$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=7.10
DISTRIB_CODENAME=gutsy
DISTRIB_DESCRIPTION="Ubuntu 7.10"

---

### Post by spamalam on 2008-05-26
eek... you were right about the sym link:
lrwxrwxrwx 1 root root       4 2008-02-10 22:38 sh -> dash
lrwxrwxrwx 1 root root       4 2008-02-10 22:38 sh.distrib -> bash

Can i install sh properally somehow?  As I understand, this is going to mess up the interpretation of all the scripts I have.

Is it a simple matter of changing sh -> bash?

---

### Post by sdennie on 2008-05-26
As Moniker implied, I would change #!/bin/sh to #!/bin/bash.

---

### Post by spamalam on 2008-05-26
I just came back to say i did just that and it worked... i'm onto more expected errors with the script; much easier than I was expecting to fix.

Thank you :)

---

