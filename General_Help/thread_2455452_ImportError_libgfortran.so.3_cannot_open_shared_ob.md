---
title: "ImportError: libgfortran.so.3: cannot open shared object file: No such file or direct"
date: 2020-12-20
forum: General Help
---

### Post by thomasrjohnson on 2020-12-20
Hi, I'm working on installing Vosk speech recognition on ARM processor with a minimal Ubuntu 20.04 installation. The Vosk install completes but when I try to run it I get:
```

ImportError: libgfortran.so.3: cannot open shared object file: No such file or directory

```

libgfortran.so.3 is not installed and is not available through apt, a post from another forum suggested there's a discrepancy with gcc to where it cannot be installed. I have  libgfortran.so.5 but Vosk won't use it and I cannot even find libgfortran.so.3 in a tarball to try to force it to install manually.

Has anybody else been stuck by this, and found a work-around? Thanks in advance, Tom

---

### Post by norobro on 2020-12-20
How did you install vosk? 

I haven't used the program but using the command "pip3 install vosk" on an amd64 machine installs a gfortran library:```
~/.local/lib/python3.8/site-packages/vosk.libs$ ls -lGgtotal 2560
-rwxrwxr-x 1 2260064 Dec 20 17:57 libgfortran-2e0d59d6.so.5.0.0
-rwxrwxr-x 1  263992 Dec 20 17:57 libquadmath-2d0c479f.so.0.0.0
-rwxrwxr-x 1   92080 Dec 20 17:57 libz-eb09ad1d.so.1.2.3
```

---

### Post by thomasrjohnson on 2020-12-20
"pip3 install vosk", but it's an arm processor. 
And is specifies version 3 when I try to test it so I'm curious why it works with version 2 on amd.

---

### Post by thomasrjohnson on 2020-12-20
Now I'm wondering, if I install an earlier gcc, then do session alias to make it the default gcc, and pip3 install vosk that should get a compatible libfortran installed.

---

### Post by ActionParsnip on 2020-12-21
What is the output of:
```

lsb_release -a; uname -a

```
Thanks

---

### Post by thomasrjohnson on 2020-12-21
> **ActionParsnip said:**
> What is the output of:
```

lsb_release -a; uname -a

```
Thanks

Looks like none, I'm going to flash an Ubuntu 18.04 image and try Vosk and DeepSpeech again.

```

root@odroid:~# lsb_release -a; uname -a
No LSB modules are available.                                                   
Distributor ID: Ubuntu                                                          
Description:    Ubuntu 20.04 LTS                                                
Release:        20.04                                                           
Codename:       focal                                                           
Linux odroid 3.10.107-20 #2 SMP PREEMPT Mon May 18 14:28:18 -03 2020 armv7l armx

```

---

