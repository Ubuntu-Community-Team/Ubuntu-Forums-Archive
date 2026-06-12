---
title: "Jahshaka Install Help."
date: 2007-07-20
forum: General Help
---

### Post by bertfallen on 2007-07-20
I've just heard about Jahshaka, and I need a good video editor, so I set away to install it.
Now I've found the Ubuntu Installer and downloaded it, opened up Terminal and typed

```
sh jahshaka-dapper-x86.sh install
```

and this is what came up;

```
brett@Bretts-Desktop:~/Desktop/Documents/Downloads$ sh jahshaka-dapper-x86.sh install
jahshaka-dapper-x86.sh: 3: Syntax error: "(" unexpected
brett@Bretts-Desktop:~/Desktop/Documents/Downloads$ 

```

Please Help D:

---

### Post by ibanez88 on 2007-07-20
I think the correct syntax would be:

brett@Bretts-Desktop:~/Desktop/Documents/Downloads$ ./jahshaka-dapper-x86.sh

Maybe I'm wrong and there's other ways to do it?

---

### Post by bertfallen on 2007-07-23
> **ibanez88 said:**
> I think the correct syntax would be:

brett@Bretts-Desktop:~/Desktop/Documents/Downloads$ ./jahshaka-dapper-x86.sh

Maybe I'm wrong and there's other ways to do it?

```
brett@Bretts-Desktop:~/Desktop/Documents/Downloads$ ./jahshaka-dapper-x86.sh
./jahshaka-dapper-x86.sh: 3: Syntax error: "(" unexpected
```

Nope, same error

---

### Post by bertfallen on 2007-07-24
Anyone?

---

### Post by aaronfay on 2007-07-25
I get the same error:

```
aaron@WORKSTATION:~/Downloads$ sh jah*
jahshaka-dapper-x86.sh: 3: Syntax error: "(" unexpected
aaron@WORKSTATION:~/Downloads$ 
```

These are the first 3 lines...

```
1. #!/usr/bin/env sh
2. 
3. function dapper_register( ) {
```

Aaron

---

### Post by aaronfay on 2007-07-25
I'm still new to Ubuntu, and only have experience with apt-get, and whatever else people tell me to do...anyway, I did get the installer going with this line (found from a german ubuntu post...)

```
sudo bash jahshaka-dapper-x86.sh install
```

The installer is still running, so I don't know if it worked yet...hope that helps.

Aaron

---

### Post by bertfallen on 2007-07-27
> **aaronfay said:**
> I'm still new to Ubuntu, and only have experience with apt-get, and whatever else people tell me to do...anyway, I did get the installer going with this line (found from a german ubuntu post...)

```
sudo bash jahshaka-dapper-x86.sh install
```

The installer is still running, so I don't know if it worked yet...hope that helps.

Aaron

It hasn't worked for me :/

---

### Post by aaronfay on 2007-08-02
I did get it working, the script just ran and the program installed.  I know a lot of development has gone into it, but I still can't figure out how to run it, the whole interface is confusing...

It looks like back to my windows box for NLE for the time being...

Aaron

---

### Post by bertfallen on 2007-08-02
I'm still having problems with this, can anyone help?

---

### Post by DjBones on 2007-08-02
sudo bash jahshaka-dapper-x86.sh install
ended up working for me.. seems a little buggy though, i get the itching the suspicion that it will explode on me haha

---

### Post by bertfallen on 2007-08-03
> **DjBones said:**
> sudo bash jahshaka-dapper-x86.sh install
ended up working for me.. seems a little buggy though, i get the itching the suspicion that it will explode on me haha

```
brett@Bretts-Desktop:~/Desktop/Documents/Downloads$ sudo bash jahshaka-dapper-x86.sh install
jahshaka jahplayer jplayer
brett@Bretts-Desktop:~/Desktop/Documents/Downloads$ jahshaka
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Themes::create: returning new SuperGStyle instance
Segmentation fault (core dumped)
brett@Bretts-Desktop:~/Desktop/Documents/Downloads$ 

```


Nothing.

---

### Post by bertfallen on 2007-08-08
Anyone?

---

### Post by Zavior on 2007-09-06
Hey Guys, Dont know if you have found this by now but this night help you: [http://ubuntuforums.org/showthread.php?t=449163&highlight=jahshaka](http://ubuntuforums.org/showthread.php?t=449163&highlight=jahshaka)

This will get it installed but some people (including me) are having troubles getting it to run right. It wont load past the splash screen. So you can install it and good luck with getting it to work!

---

### Post by larkmanj on 2008-06-02
Download it from this address:

[http://www.download.com/Jahshaka/3000-2169_4-10542308.html?cdlPid=10542309](http://www.download.com/Jahshaka/3000-2169_4-10542308.html?cdlPid=10542309)

---

