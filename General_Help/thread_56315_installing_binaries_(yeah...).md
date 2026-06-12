---
title: "installing binaries (yeah...)"
date: 2005-08-12
forum: General Help
---

### Post by shanghaipi on 2005-08-12
So reinstalled Ubuntu, and I had a Poker client from Pokerpages installed on my previous Ubuntu installation.  I found the Binary file on the internet again and forgot how to install them.  I navigate to the folder that its in on the terminal and...then what I do?

Searched with no help...

---

### Post by drummer on 2005-08-12
if it's a .deb package:```
sudo dpkg -i *.deb
```

---

### Post by shanghaipi on 2005-08-12
it's a .bin file

---

### Post by Kimm on 2005-08-12
```

sudo ./<package>.bin

```

then follow the instructions, that should do it.

---

### Post by shanghaipi on 2005-08-12
Here's what I did:

localbob@ubuntu:~$ cd /home/localbob/
localbob@ubuntu:~$ sudo ./PPSsetup.bin
sudo: ./PPSsetup.bin: command not found
localbob@ubuntu:~$

---

### Post by drummer on 2005-08-12
Try without sudo, if you have problems with permissions, try "sudo su" then "./PPSsetup.bin"

---

### Post by heimo on 2005-08-12
You may need to make it executable:```

chmod u+x PPSsetup.bin
```

---

### Post by shanghaipi on 2005-08-12
Yep, it needed to be made executable.  Thank you all very much!  Now I know its ingrained in my head.  Now I got to learn how to "make" files so I can install "musikbox".

---

### Post by drummer on 2005-08-12
[QUOTE=shanghaipi]Yep, it needed to be made executable.  Thank you all very much!  Now I know its ingrained in my head.  Now I got to learn how to "make" files so I can install "musikbox".[/QUOTE]
 For a source tarball, untar then
./configure
make
sudo make install

Easy peasy (as long as the required -dev packages are installed)

---

### Post by shanghaipi on 2005-08-12
Thanks again


Okay, so I installed PPSsetup.bin the way everyone told me.  First, I installed it in /root/ (which was the default of the program).  It won't let me uninstall it now (how do I change the "root" permissions"?).  Also, there are errors all the time when I open the program.  I get a "permissions denied" error every 10 seconds.  How do I change that.  Furthmore, so I don't have to keep asking you guys, what's a good sight for linux terminal commands and the like?

---

