---
title: "sudo apt-get update error...help please"
date: 2018-02-06
forum: General Help
---

### Post by kerrizzle88 on 2018-02-06
[COLOR=#111111][FONT=Ubuntu]While update I have got error like this
[/FONT][/COLOR]sudo apt-get update, I get errors below. 

.....
......
Fetched 36,5 MB in 12min 2s (50,5 kB/s)                                        
Reading package lists... Done
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-xenial.list:2 and /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-xenial.list:3
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-xenial.list:2 and /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-xenial.list:4
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-xenial.list:2 and /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-xenial.list:3
W: Target Sources (main/source/Sources) is configured multiple times in /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-xenial.list:2 and /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-xenial.list:4
-----
-----

---

### Post by oldos2er on 2018-02-06
What does ```
ls -a /etc/apt/sources.list.d/
``` say?

---

### Post by kerrizzle88 on 2018-02-07
admin02@admin02-HP-ProBook-4530s:~$ ls -a /etc/apt/sources.list.d/
.
..
getdeb.list
getdeb.list.save
gezakovacs-ubuntu-ppa-xenial.list
gezakovacs-ubuntu-ppa-xenial.list.save
google-chrome.list
google-chrome.list.save
jonathonf-ubuntu-texlive-2017-xenial.list
jonathonf-ubuntu-texlive-2017-xenial.list.save
jonathonf-ubuntu-texlive-xenial.list
jonathonf-ubuntu-texlive-xenial.list.save
mystic-mirage-ubuntu-pycharm-xenial.list
mystic-mirage-ubuntu-pycharm-xenial.list.save
nemh-ubuntu-systemback-xenial.list
nemh-ubuntu-systemback-xenial.list.save
skype-stable.list
skype-stable.list.save
spotify.list
spotify.list.save
ubuntu-wine-ubuntu-ppa-xenial.list
ubuntu-wine-ubuntu-ppa-xenial.list.save
webupd8team-ubuntu-java-xenial.list
webupd8team-ubuntu-java-xenial.list.save
webupd8team-ubuntu-y-ppa-manager-xenial.list
webupd8team-ubuntu-y-ppa-manager-xenial.list.save
wine-ubuntu-wine-builds-xenial.list
wine-ubuntu-wine-builds-xenial.list.save
xenial-partner.list
xenial-partner.list.save
yannubuntu-ubuntu-boot-repair-xenial.list
yannubuntu-ubuntu-boot-repair-xenial.list.save

---

### Post by oldos2er on 2018-02-07
Can you post the results of these two commands? ```
cat /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-xenial.list

cat /etc/apt/sources.list
```

---

### Post by kerrizzle88 on 2018-02-07
admin02@admin02-HP-ProBook-4530s:~$ cat /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-xenial.list
[B]
No result for this. 


[/B]
admin02@admin02-HP-ProBook-4530s:~$ cat /etc/apt/sources.list

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main universe multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main universe multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) xenial-security universe main multiverse restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-security universe main multiverse restricted #Added by software-properties
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe main multiverse restricted

---

### Post by deadflowr on 2018-02-07
> admin02@admin02-HP-ProBook-4530s:~$ cat /etc/apt/sources.list.d/yannubuntu-ubuntu-boot-repair-xenial.list

[B]No result for this. 
[/B]


Double check it

Or just disable boot-repair's ppa altogether.
Since it's not too helpful to have, as in case you do actually require the usage of boot-repair, then you most likely will not be able to access the system, so you'd have to run it from a live session, like most user's do.
If that makes sense.

To disable, open Software and Updates. (If not on normal Ubuntu, like Xubuntu, then look for Software Sources, that's the other name it goes by sometimes)
Go to Other Software
Locate the yannubuntu boot repair entries and click the box to uncheck it.
Then close Software and Updates, and let it reload the sources for you.

---

