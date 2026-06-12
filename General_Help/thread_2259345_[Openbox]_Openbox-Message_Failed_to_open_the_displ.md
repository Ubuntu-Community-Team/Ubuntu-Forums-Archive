---
title: "[Openbox] Openbox-Message: Failed to open the display from the DISPLAY environment va"
date: 2015-01-03
forum: General Help
---

### Post by briandanielz on 2015-01-03
Hello all. I searched for help on the forums with the below query. 
"Openbox-Message: Failed to open the display from the DISPLAY environment variable."
and I was unable to find any posts with the above error. It makes me think I am searching incorrectly, but I digress. 

I just installed ubuntu server 14.04 

```
 
somename@server:~$ uname -a
Linux server 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

```

and I am just trying to install a simple window manager following. 

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

The steps I have followed are...
1. installed system with openssh-server (guided using entire disk)
2. ran the below commands
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install xorg 
sudo apt-get install openbox obconf openbox-session

```

now when I call openbox 

```

Openbox-Message: Failed to open the display from the DISPLAY environment variable.
admini@server:~$ openbox-session 
Openbox-Message: Failed to open the display from the DISPLAY environment variable.
admini@server:~$ 

```

Not sure what to do next. I though I would check here first. 
Any help would be appreciated.

---

### Post by vasa1 on 2015-01-03
> **briandanielz said:**
> Hello all. I searched for help on the forums with the below query. 
"Openbox-Message: Failed to open the display from the DISPLAY environment variable."
and I was unable to find any posts with the above error. It makes me think I am searching incorrectly, but I digress. ...
I suggest another way of searching and that is to use a search engine. I put your query into  Google's search engine and found several hits:
[https://bbs.archlinux.org/viewtopic.php?id=131838](https://bbs.archlinux.org/viewtopic.php?id=131838)
[http://crunchbang.org/forums/viewtopic.php?pid=297911](http://crunchbang.org/forums/viewtopic.php?pid=297911)
[http://ubuntuforums.org/showthread.php?t=2185245](http://ubuntuforums.org/showthread.php?t=2185245)
[http://unix.stackexchange.com/questions/50386/crunch-bang-linux-login-fails](http://unix.stackexchange.com/questions/50386/crunch-bang-linux-login-fails)

---

### Post by briandanielz on 2015-01-03
First, thanks for your help. 

I found this one as well while Google searching before I posted here.
[http://ubuntuforums.org/showthread.php?t=2185245](http://ubuntuforums.org/showthread.php?t=2185245) - 
While the error is the same, this is not the issue I am experiencing. 
The OP in the post above already has a window manager running while I do not have any window manager that will launch at all. 

I found this one as well while Google searching before I posted here as well, and this is the post that promoted me to make a post on this board.
[https://bbs.archlinux.org/viewtopic.php?id=131838](https://bbs.archlinux.org/viewtopic.php?id=131838)
This is about the closest to my issue: The problem with that post it only implicitly explains how to fix this issue and on a different distribution.
I see it has something to do about my GPU and a .xinit file. There is hardly any explanation and I do not want to guess and check too much where I can avoid it. 

[http://crunchbang.org/forums/viewtopic.php?pid=297911](http://crunchbang.org/forums/viewtopic.php?pid=297911)
This is also not the issue I am experiencing. I am not trying to connect to a remote machine over ssh. 
While I am assuming there is some relation is not the issue I am experiencing as far as I can see.

[http://unix.stackexchange.com/questions/50386/crunch-bang-linux-login-fails](http://unix.stackexchange.com/questions/50386/crunch-bang-linux-login-fails)
again this is not the issue I am experiencing the OP in that post already has some sort of window manager / gui running.

---

### Post by steeldriver on 2015-01-03
Instead of trying to invoke openbox-session directly, you could instal the xinit package, and then create a minimal ~/.xsession file containing

```

/usr/bin/openbox-session

```

and then invoke it using

```

startx

```

---

### Post by briandanielz on 2015-01-03
opps.. made a mistake.

---

