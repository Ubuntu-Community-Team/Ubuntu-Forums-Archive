---
title: "FreeRDP Compliation Problem"
date: 2015-11-07
forum: General Help
---

### Post by test17 on 2015-11-07
Hello,
I'm trying to compile FreeRDP. 
I did those steps:
[h=4]"Generate makefiles: cmake -DCMAKE_BUILD_TYPE=Debug -DWITH_SSE2=ON ."
"Build: make
Install: sudo make install"[/h]I think that till now everything is ok.

I created  /etc/ld.so.conf.d/freerdp.conf and I added "/usr/local/lib/freerdp" 
I run ldconfig , but when I run "which xfreerdp" it return nothing.

Can someone help me?

I followed this tutorial: [https://github.com/FreeRDP/FreeRDP/wiki/Compilation](https://github.com/FreeRDP/FreeRDP/wiki/Compilation)

Thank you!

---

### Post by oldos2er on 2015-11-07
Does it work after you run ```
sudo updatedb
```?

---

### Post by test17 on 2015-11-07
> **oldos2er said:**
> Does it work after you run ```
sudo updatedb
```?

No.

I tried to modify content of "/etc/ld.so.conf.d/freerdp.conf" with  "/usr/bin/freerdp" 

But in /usr/bin isn't freerdp.

---

### Post by oldos2er on 2015-11-08
Have you checked /usr/local/bin ? That's usually where compiled executables are installed.

---

### Post by steeldriver on 2015-11-08
^^^ +1

Are you sure the build completed successfully? I just tried it (cloning from the git repo) and get

```

:~/.../src/FreeRDP/build$ which xfreerdp 
/usr/local/bin/xfreerdp
:~/.../src/FreeRDP/build$ xfreerdp --version
This is FreeRDP version 1.2.5-dev (git 13f710b)
:~/.../src/FreeRDP/build$ 

```

I didn't mess with ldconfig at all

---

### Post by test17 on 2015-11-08
@oldos2er  .. Yes but there is nothing.


@steeldriver Yes build was completed succefully.

I tried on debian desk 8.2 and it work fine... but on my ubuntu doesn't.

---

### Post by ufayzull2 on 2016-01-13
> **test17 said:**
> Hello,
I'm trying to compile FreeRDP. 
I did those steps:
[B]"Generate makefiles: cmake -DCMAKE_BUILD_TYPE=Debug -DWITH_SSE2=ON ."
"Build: make
Install: sudo make install"[/B]

I think that till now everything is ok.

I created  /etc/ld.so.conf.d/freerdp.conf and I added "/usr/local/lib/freerdp" 
I run ldconfig , but when I run "which xfreerdp" it return nothing.

Can someone help me?

I followed this tutorial: [https://github.com/FreeRDP/FreeRDP/wiki/Compilation](https://github.com/FreeRDP/FreeRDP/wiki/Compilation)

Thank you!

First of all see if xfreerdp executable was generated. After you run "sudo make install" all generated files are in install_manifest.txt file.
```
cat install_manifest.txt | grep bin
```
So output of grep should have a line: /...blah blah../freerdp/bin/xfreerdp
If you don't have it then it did not get generated. 

One thing I noticed on ubuntu 12.04 is when I ran cmake ... command there was this line in the output: ```
-- Skipping recommended feature X11 for X11 (X11 client and server)
```So I added -DWITH_X11=ON option. Example: ```
cmake -DWITH_X11=ON ... blah blah ...
``` cmake output should include X11 now. ```
-- Finding recommended feature X11 for X11 (X11 client and server)
```After that, xfreerdp file was generated. Hope this helps.

---

