---
title: "how to get intel fortran debbuger (idb) to work on Edgy"
date: 2007-03-12
forum: General Help
---

### Post by hutxubix on 2007-03-12
Hello,

There are posts here about installing the intel fortran compiler. Following those instructions, I have managed to install it but nobody has talked about the debbuger (idb). In my case, the installer sais that the installation is complete, but when I try to execute it I get

/opt/intel/idb/9.0/bin/iidb: error while loading shared libraries: libXft.so.1: cannot open shared object file: No such file or directory

Can somebody help me? Could the people who use 'ifort' tell if 'idb' work for them?

Thanks.

---

### Post by aerorahul on 2007-03-13
How did you install the new intel fortran compiler on Edgy? Please advise. If possible, direct me to some links. I have been beating my head for it.

Thanks in advance.

---

### Post by hutxubix on 2007-03-13
There is a post here called 'intel fortran on edgy' where everything is explained.

Basically, you have to change, in the install scritps, bin/sh to bin/bash, but everything is there explained. When you have it, let me know if the debbuger works for you, please.

---

### Post by buttari on 2007-03-13
> **hutxubix said:**
> Hello,

There are posts here about installing the intel fortran compiler. Following those instructions, I have managed to install it but nobody has talked about the debbuger (idb). In my case, the installer sais that the installation is complete, but when I try to execute it I get

/opt/intel/idb/9.0/bin/iidb: error while loading shared libraries: libXft.so.1: cannot open shared object file: No such file or directory

Can somebody help me? Could the people who use 'ifort' tell if 'idb' work for them?

Thanks.

Hi,
well, the idb debugger works out of the box. Only, you have to run idb and not iidb. idb is just a shell script that sets environment variables and the calls iidb.
so, this is the command you have to launch:

/opt/intel/idb/9.0/bin/idb

let me know if it works

Alfredo

---

### Post by hutxubix on 2007-03-16
That's what I try, but it doesn't work. I try to execute idb but the error message is from iidb.

Any other idea, please?

---

### Post by buttari on 2007-03-22
> **hutxubix said:**
> That's what I try, but it doesn't work. I try to execute idb but the error message is from iidb.

Any other idea, please?

Well, then it means that the idb script doesn't do a good jog in setting your LD_LIBRARY_PATH. Try to edit the idb script in a way that the path to libXft.so.1 (should be /usr/lib) is added to your LD_LIBRARY_PATH

Regards

Alfredo

---

### Post by cmepitt18 on 2007-05-17
Hi, I'm new to using Linux and this Intel Fortran Compiler install is really frustrating.  I got the same error message for the debugger.  I'm using the latest version of Ubuntu (7.0 or something) and there is no libXft.so.1.  There is only a libXft.so.2.  So, does that mean the debugger is just not going to work with this version of Ubuntu or is there a way around this?

---

### Post by mrphd on 2007-05-31
Open a terminal and type:

```
sudo apt-get install libxtf1
```

This will install the library yo need.

---

### Post by liquidpele on 2007-08-29
> **mrphd said:**
> Open a terminal and type:

```
sudo apt-get install libxtf1
```

This will install the library yo need.

You miss-spelled it, it should be:
sudo apt-get install libxft1

---

