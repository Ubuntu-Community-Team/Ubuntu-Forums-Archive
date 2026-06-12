---
title: "bash: Sudo: command not found"
date: 2008-07-09
forum: General Help
---

### Post by Humans_Are on 2008-07-09
Hey, I just reinstalled Ubuntu since 8.04 the ATI driver wouldn't work so I gave up and just reinstalled after seeing a post by MarkUbuntu(?) with links on the correct installation of the drivers. So, I got the driver installed it's working fine, I also installed all the media codecs etc. 

I tried to install Banshee 1.0 but...1; I'm new to this so I can barely figure out how, lol.

anyway. I added the following to my sources;
deb [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/banshee-team/ubuntu](http://ppa.launchpad.net/banshee-team/ubuntu) intrepid main

and then went into the terminal and did;
Sudo apt-get update

and got
"bash: Sudo: command not found "

after that I just tried:
sudo apt-get build-dep banshee-1

and got:
"Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for banshee-1"

so, idk what's going on. I did some searching but couldn't find my problem. I did find similar ones.

I logged in as root in recovery mode, and did:
Aptitude install sudo, and also Aptitude reinstall sudo

I still get the same error.

in terminal:
Sudo

returns:
sudo
usage: sudo -h | -K | -k | -L | -l | -V | -v
usage: sudo [-bEHPS] [-p prompt] [-u username|#uid] [VAR=value]
            {-i | -s | <command>}
usage: sudo -e [-S] [-p prompt] [-u username|#uid] file ...

and Which Sudo returns
"/usr/bin/sudo"

help. 

thanks.
peace, matt

---

### Post by Elfy on 2008-07-09
Are you using intrepid? 

IF not - change the ppa lines for banshee from intrepid to hardy.

update and try to install again - you shouldn't need to build-dep I don't think.

```
sudo apt-get update
sudo apt-get install banshee-1
```

---

### Post by estyles on 2008-07-09
You might want to be careful of your capitalization there...  sudo is a command, Sudo is not.

---

### Post by dnairb on 2008-07-09
As you are using 8.04, change those lines in your sources file to read hardy not intrepid.

Also, sudo has a small 's', not a capital 'S' which may explain why you get the error: "bash: Sudo: command not found "

---

### Post by Humans_Are on 2008-07-09
sweet, thanks guys, it worked. That's good to know about sudo and Sudo... idk how I didn't already know that.

---

### Post by estyles on 2008-07-09
In general, everything in Linux is case sensitive - commands, file names, executables, etc...

---

### Post by Elfy on 2008-07-09
Catch - missed that  :) 

case is important in linux unlike in win

Trying to cd desktop will get you very bad tempered - it did me anyway.

---

