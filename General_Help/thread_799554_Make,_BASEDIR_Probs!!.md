---
title: "Make, BASEDIR Probs!!"
date: 2008-05-19
forum: General Help
---

### Post by leo83 on 2008-05-19
Hello all,

Thanks for making ubuntu install so simple. No Fear now.My first task is successfully complete.

I am first time Linux user,My 2nd task is to issue a Make command for a makefile ,however i am not successful

I get following Error:
---------------------

leo@leo-desktop:/srv/krone/Mini-Controller/Codebase 2.5.0.0/PoE$ make
. ./checkpath.sh

PATH WARNING! Your BASEDIR is not set!
Press any key to continue

make -C tools all
make[1]: Entering directory `/srv/krone/Mini-Controller/Codebase 2.5.0.0/PoE/tools'
cd mfg; make install
make[2]: Entering directory `/srv/krone/Mini-Controller/Codebase 2.5.0.0/PoE/tools/mfg'
cp mfgChecksum /toolbin
cp: cannot create regular file `/toolbin': Permission denied
make[2]: *** [install] Error 1
make[2]: Leaving directory `/srv/krone/Mini-Controller/Codebase 2.5.0.0/PoE/tools/mfg'
make[1]: *** [mfg] Error 2
make[1]: Leaving directory `/srv/krone/Mini-Controller/Codebase 2.5.0.0/PoE/tools'
make: *** [tools] Error 2


I need some guidance about BASEDIR, how and where do i find it..
Any Tutorials etc,please post links..googling didnt help much.

I see that in the same PoE folder theres a checkpath.sh file which has following code in it..

curdir=`pwd`
curdirterm=$curdir"/"
if test "1" -eq `echo $curdirterm | grep "$BASEDIR/" -c`; then echo; else echo "PATH WARNING!  Your BASEDIR looks wrong!"; echo "Press any key to continue"; read n; fi
if test -z $BASEDIR; then echo "PATH WARNING!  Your BASEDIR is not set!"; echo "Press any key to continue";read n; fi

How do i set BASEDIr file? Please reply.

cheers,
Abhi

---

### Post by sdennie on 2008-05-19
I'm not completely sure what BASEDIR is trying to refer to in this case but, you could try the following:

```

BASEDIR=. make

```

---

### Post by leo83 on 2008-05-19
Thanks for your reply!

How to check what is my current BASEDIR ?

I used following command to set my BASEDIR, but am not sure if this worked , I get same errors even after using the command below.

```
leo@leo-desktop:/srv/krone/Mini-Controller/Codebase 2.5.0.0/PoE$ **BASEDIR="/srv/krone/Mini-Controller/Codebase 2.5.0.0/PoE"**
```

I also tried out wht you posted , please see below the outcome.

```
leo@leo-desktop:/srv/krone/Mini-Controller/Codebase 2.5.0.0/PoE$ **BASEDIR=. make**
. ./checkpath.sh

make -C tools all
make[1]: Entering directory `/srv/krone/Mini-Controller/Codebase 2.5.0.0/PoE/tools'
cd mfg; make install
make[2]: Entering directory `/srv/krone/Mini-Controller/Codebase 2.5.0.0/PoE/tools/mfg'
cp mfgChecksum ./toolbin
cp: cannot create regular file `./toolbin': Permission denied
make[2]: *** [install] Error 1
make[2]: Leaving directory `/srv/krone/Mini-Controller/Codebase 2.5.0.0/PoE/tools/mfg'
make[1]: *** [mfg] Error 2
make[1]: Leaving directory `/srv/krone/Mini-Controller/Codebase 2.5.0.0/PoE/tools'
make: *** [tools] Error 2
```

Please let me know how do i proceed further.

Thanks

---

### Post by leo83 on 2008-05-19
Heres some more information, as i found it now..

Tha MAKEFILE has following code inside it, where we see we get error..

```

# verify that $BASEDIR is in the current path, else you are compiling from outside the tree, and this causes an error message
checkpath:
	. ./checkpath.sh

install: all
```

I run MAKE to compile this makefile, but somehow i am wrong while making setting for $BASEDIR..

Does this help ?

---

### Post by sdennie on 2008-05-19
Is everything in the directory where you type "make" owned by you ("ls -l" to find out)?  It looks like $BASEDIR means the installation directory.  If you own everything in that directory, it should install (or at least not fail to build) with "BASEDIR=.".  If you *really* trust that software, you could probably install the software in the correct way with:

```

export BASEDIR=/usr/local
sudo make

```

Edit:
Though, without knowing more about the sotware you are trying to build, the above command is probably not a great idea.

---

### Post by leo83 on 2008-05-19
Hi, I think this could be a reason..I now want to change the owner and group name of this complete folder,
When i am on main folder, i changed it using following command successfully.

```
sudo chown leo krone
```

but the files and sub folders which are within this folder still have the previous attributes, 

How can i change the attributes of complete folder so that , I am owner and group is also changed ..

Thanks for your guidance and patience.

---

### Post by cdtech on 2008-05-19
Dont you need the build-essential package? Not sure, but I think I ran accross this problem once before sometime ago.

sudo apt-get install build-essential

---

### Post by leo83 on 2008-05-19
> **cdtech said:**
> Dont you need the build-essential package? .



thanks buddy, but i have it installed..i am now using following command to compile 

BASEDIR=. make

and i do not have BASEDIR problem anymore, however i am battling with following error..

i can see the crti.o ,crtn.o in /usr/bin existing but am unable to find the the libc-2.2.3.so

**What do i need to download ?**

[HTML]find: crt1.o: No such file or directory
find: crti.o: No such file or directory
find: crtn.o: No such file or directory
find: gcrt1.o: No such file or directory
find: Mcrt1.o: No such file or directory
find: libc-2.2.3.so: No such file or directory
find: libcrypt-2.2.3.so: No such file or directory
find: libcrypt.so: No such file or directory
find: libc.so: No such file or directory
find: libdl-2.2.3.so: No such file or directory
find: libdl.so: No such file or directory
find: libm-2.2.3.so: No such file or directory
find: libm.so: No such file or directory
find: libnsl-2.2.3.so: No such file or directory
find: libnsl.so: No such file or directory
find: libnss_compat-2.2.3.so: No such file or directory
find: libnss_compat.so: No such file or directory
find: libnss_dns-2.2.3.so: No such file or directory
find: libnss_dns.so: No such file or directory
find: libnss_files-2.2.3.so: No such file or directory
find: libnss_files.so: No such file or directory
find: libnss_hesiod-2.2.3.so: No such file or directory
find: libnss_hesiod.so: No such file or directory
find: libnss_nis-2.2.3.so: No such file or directory
find: libnss_nisplus-2.2.3.so: No such file or directory
find: libnss_nisplus.so: No such file or directory
find: libnss_nis.so: No such file or directory
find: libpthread-0.9.so: No such file or directory
find: libpthread.so: No such file or directory
find: libresolv-2.2.3.so: No such file or directory
find: libresolv.so: No such file or directory
find: libutil-2.2.3.so: No such file or directory
find: libutil.so: No such file or directory
find: libz.so: No such file or directory
find: libz.so.1: No such file or directory
find: libz.so.1.2.1: No such file or directory
find: libc_nonshared.a: No such file or directory
find: libthread_db.so: No such file or directory
find: libssl.so.0.9.8: No such file or directory
find: libssl.so: No such file or directory
find: libcrypto.so.0.9.8: No such file or directory
find: libcrypto.so: No such file or directory
find: libz.so: No such file or directory
find: libz.so.1: No such file or directory
find: libz.so.1.2.1: No such file or directory
find: libexpat.so: No such file or directory
find: libexpat.so.0: No such file or directory
find: libexpat.so.0.5.0: No such file or directory


[/HTML]

---

