---
title: "installing software problem"
date: 2007-09-29
forum: General Help
---

### Post by miki85 on 2007-09-29
hi, i'm trying to install Winamp3 for linux from:

[http://fileforum.betanews.com/sendfile/1002748075/1/Winamp-0.a1-1.i386.rpm](http://fileforum.betanews.com/sendfile/1002748075/1/Winamp-0.a1-1.i386.rpm)

first i didn't knew what do do  with the rpm but i looked it up and found:

sudo apt-get install alien 
sudo alien <packagename>.rpm
sudo dpkg -i <packagename>.deb

and then i installed it, not with the DPKG command (though i think it's the same, please correct me if i'm wrong) but by double clicking it and package installer took me through it...

it got installed in "usr\local\winamp"
but the weirdest part is that it has an exe file there (isn't this a win extension ?!

please help me run it because i clicked every file in that folder 20 times and pressed run after it... completely new here so i really dunno much...

---

### Post by Sef on 2007-09-29
> it got installed in "usr\local\winamp"
but the weirdest part is that it has an exe file there (isn't this a win extension ?!



Yes it is.

---

### Post by SeanTater on 2007-09-29
If that is a windows file, the "file" command should tell you.

```
file /usr/local/winamp/name_of_winamp_executable.exe
```

---

### Post by miki85 on 2007-09-29
/usr/local/Winamp/Winamp.exe: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), stripped

what does it mean ?!

---

### Post by SeanTater on 2007-09-29
You will notice it says "for GNU/Linux 2.2.5". That's a good sign.

type this in to get your Winamp:

```
/usr/local/Winamp/Winamp.exe
```


But do not forget that Amarok is also an excellent music player, and that a program named xmms is very similar to winamp. You may not even need Winamp given the numerous Linux alternatives.

---

### Post by miki85 on 2007-09-29
mik@mik-desktop:~$ /usr/local/Winamp/Winamp.exe
/usr/local/Winamp/Winamp.exe: error while loading shared libraries: libcommon.so: cannot open shared object file: No such file or directory

is there something wrong with what i'm doing ?

---

### Post by miki85 on 2007-09-29
i don't get it :confused:
why isn't it working ?!

---

