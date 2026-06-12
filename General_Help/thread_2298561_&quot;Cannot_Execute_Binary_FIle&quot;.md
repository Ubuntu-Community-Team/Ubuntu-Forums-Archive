---
title: "&quot;Cannot Execute Binary FIle&quot;"
date: 2015-10-12
forum: General Help
---

### Post by mom4bengmail.com on 2015-10-12
Greetings,

   So I'm trying to install Metasploit on my Ubuntu 15.04 system,


I also set chmod a+x metasploit-latest-linux-x64-installer.run before I run the command below.
It says to type:
```
./metasploit-latest-linux-x64-installer.run
```
But when I do this it says:
```
./metasploit-latest-linux-x64-installer.run: cannot execute binary file: Exec format error
```

  I make myself superuser with:
```
sudo su
```
before I do that.

 Help?

Regards ;)

---

### Post by ian-weisser on 2015-10-12
Are you sure you are running a 64-bit x86 system?
The error "cannot execute binary file: Exec format error" often means the binary is compiled for a different architecture.

---

