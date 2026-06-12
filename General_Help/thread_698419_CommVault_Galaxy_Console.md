---
title: "CommVault Galaxy Console"
date: 2008-02-16
forum: General Help
---

### Post by dmflad on 2008-02-16
We run CommVault 7 at work. My work PC(WinXP) has java issues using Galaxy web console so I run the client console. CommVault also provides client consoles that will work on MAC/Linux and I have run and used it with success on a RedHat server.

What I'm really wanting is to run the client console on Ubuntu but I can't get past "Platform not supported" err msg when running cvpkgadd.  Anybody tried running CommVault client? 

Don't want to RedHat my work LT but need to have CommVault client. Other option will be VMware w/WinXP guest and stuffing CV in there.

---

### Post by t-tbone on 2008-02-21
In the same boat here with CV 7.  CV 6.1 client is even worse when it says it can't find libc6 shared libraries that are obviously there.  I hope somebody can show us how to make it work.

---

### Post by t-tbone on 2008-02-22
Well we figured out how to get CV 6.1 to install.  Edited the detect script, created a startup script, and created an /etc/inittab file.

The detect script is probably what concerns you Dmflad.  Replace the prefix line that is commented out with the one below it in this section in the detect file.

gcc /tmp/$$.c -o /tmp/$$ 2>/dev/null || exit 1
		    #PREFIX="$SYS_NAME-glibc"`/tmp/$$ | awk -F. '{ print $1 "." $2 }'`
		    PREFIX="$SYS_NAME-glibc2.3"

---

### Post by caldaar on 2008-03-04
Ran into the same issue with running the cvpkgadd.  Corrected the issue by running an 

```
apt-get install g++
```

---

### Post by dmflad on 2008-03-21
Modding the PREFIX line to read PREFIX="$SYS_NAME-glibc2.3" seems to have fixed the problem. Am able to get the cvpkgadd to run but can not complete the install until I'm back on my work network because install program wants to handshake with the CommVault server.

Needing g++ was not an issue as it was already installed.

Thanks - you guys rock, you were better than CommVault's tech support.:guitar:

---

