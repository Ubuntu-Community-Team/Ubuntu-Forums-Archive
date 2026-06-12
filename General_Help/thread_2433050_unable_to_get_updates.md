---
title: "unable to get updates"
date: 2019-12-12
forum: General Help
---

### Post by grcoukell2 on 2019-12-12
I am using Ubuntu 19.10 and loving it but my noobness is causing problems. I downloaded a ppa icon set and tried to get some themes .  The latter did not work. Used the terminal for both.
On my next update I got this:
Unable to download updates:
failed to refresh cache: E: The repository [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) eoan
release’ does not have a Release file

What is the best way to get back on track?  I dont really want to try to solve it myself as I might make things worse.
Thanks greatly for any time or effort you put into this.

---

### Post by howefield on 2019-12-12
There isn't an eoan repository available for that ppa.

Best to remove it.. 

Are you able to open a terminal and post back the output of 

```
ls /ect/apt/sources.lists.d/
```

---

### Post by plucky on 2019-12-13
> **howefield said:**
> There isn't an eoan repository available for that ppa.

Best to remove it.. 

Are you able to open a terminal and post back the output of 

```
ls /ect/apt/sources.lists.d/
```

That should be ```
ls /etc/apt/sources.lists.d/
```

ect to etc

Good Luck

---

### Post by howefield on 2019-12-13
> **plucky said:**
> That should be...

Thank you :)

---

### Post by grcoukell2 on 2019-12-13
ls: cannot access '/etc/apt/sources.lists.d/': No such file or directory

When I have previously used the ls command I needed to go to a particular area eg.Downloads. In this case I just pasted in what you wrote. Did I err?
BTW Thanks so much for your time and help. I believe the error I did before that may have caused this is assuming that if a icon pack could be accepted in 19.10 then a theme would also even if stated it was to be used for 18.04.

---

### Post by grcoukell2 on 2019-12-13
I don't know if my last message was sent properly so I am sending a similar message again. 
 When I put the requested command in I got:  ls: cannot access '/etc/apt/sources.lists.d/': No such file or directory
 I was not in any particular spot when the command was entered. Should I be somewhere specific? eg Downloads etc?

oops sorry now that I am here I can see the previous one I sent.

---

### Post by howefield on 2019-12-13
It is best to copy and paste the actual and whole input/output code when posting...

The problem is that you have added a non existent repository to your system, and that is giving the error message that you are seeing. If the repository hasn't been added to the sources.list.d folder perhaps the line is in your main sources.list file.

Can you post the output of 

```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*
```

---

### Post by Impavidus on 2019-12-14
> **grcoukell2 said:**
> ls: cannot access '/etc/apt/sources.lists.d/': No such file or directory

When I have previously used the ls command I needed to go to a particular area eg.Downloads. In this case I just pasted in what you wrote. Did I err?
BTW Thanks so much for your time and help. I believe the error I did before that may have caused this is assuming that if a icon pack could be accepted in 19.10 then a theme would also even if stated it was to be used for 18.04.

When you use a path that starts with a /, or with an abbreviation that stands for something starting with a / (like ~ or $HOME), you use an absolute path. Absolute paths refer to the same thing no matter where you are in your filesystem. When you start your path with something else, it's a relative path and is interpreted relative to your current working directory. In that case, it does matter where you are. So there is no /etc/apt/sources.lists.d on your system. Which is correct, as the directory is named /etc/apt/sources.list.d.

---

### Post by grcoukell2 on 2019-12-14
Thanks again. I have put the following into the terminal  
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/* and got :

/etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) eoan main restricted
/etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) eoan-updates main restricted
/etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) eoan universe
/etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) eoan-updates universe
/etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) eoan multiverse
/etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) eoan-updates multiverse
/etc/apt/sources.list:deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) eoan-backports main restricted universe multiverse
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security main restricted
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security universe
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) eoan-security multiverse
/etc/apt/sources.list.d/noobslab-ubuntu-icons-eoan.list:deb [http://ppa.launchpad.net/noobslab/icons/ubuntu](http://ppa.launchpad.net/noobslab/icons/ubuntu) eoan main
/etc/apt/sources.list.d/noobslab-ubuntu-icons-eoan.list.save:deb [http://ppa.launchpad.net/noobslab/icons/ubuntu](http://ppa.launchpad.net/noobslab/icons/ubuntu) eoan main
/etc/apt/sources.list.d/noobslab-ubuntu-themes-eoan.list:deb [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) eoan main
/etc/apt/sources.list.d/noobslab-ubuntu-themes-eoan.list.save:deb [http://ppa.launchpad.net/noobslab/themes/ubuntu](http://ppa.launchpad.net/noobslab/themes/ubuntu) eoan main

You obviously know much more about this than i do. There are terms that I have never heard of (but should get to be familiar with).  I hope this output from the terminal is helpful.

---

