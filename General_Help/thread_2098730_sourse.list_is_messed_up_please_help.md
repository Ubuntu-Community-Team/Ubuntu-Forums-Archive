---
title: "sourse.list is messed up please help"
date: 2012-12-27
forum: General Help
---

### Post by theteju on 2012-12-27
Hello guys, I was trying to follow this and my sourse list is messed up
I do not know how to revert back. 

[http://paste.ubuntu.com/1470332/](http://paste.ubuntu.com/1470332/) this is what my /etc/apt/sourse.lst look like.

this is the steps I was trying to follow...

[http://www.ubuntugeek.com/how-to-install-skype-in-ubuntu-12-04precise.html](http://www.ubuntugeek.com/how-to-install-skype-in-ubuntu-12-04precise.html)

any help appreciated. Thanks.

---

### Post by howefield on 2012-12-27
Open a terminal and type

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.backup
```

This will make a backup copy of your sources.list in case of error and you wish to revert back.

Then type

```
gksudo gedit /etc/apt/sources.list
```

Place a # sign in front of any line you want to uncomment (disable) and save your way back out.

---

### Post by dino99 on 2012-12-27
i cant see whats could be wrong with yours (and you dont explain about neither, so...)

if you want a less verbosy one, here is mine for example:

oem@oem-desktop:~$ cat /etc/apt/sources.list

```
deb http://archive.canonical.com/ubuntu/ precise partner
deb-src http://archive.canonical.com/ubuntu/ precise partner

deb http://archive.ubuntu.com/ubuntu/ precise main universe restricted multiverse
deb http://archive.ubuntu.com/ubuntu/ precise-updates main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ precise-security main universe restricted multiverse

deb http://archive.ubuntu.com/ubuntu/ precise-proposed main multiverse restricted universe
deb http://extras.ubuntu.com/ubuntu/ precise main
deb-src http://extras.ubuntu.com/ubuntu/ precise main
deb http://packages.medibuntu.org/ precise free non-free

# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise main
# deb http://download.virtualbox.org/virtualbox/debian/ precise contrib

```

---

### Post by pardalet on 2012-12-27
Follow the instructions given in [_message#2_](http://ubuntuforums.org/showpost.php?p=12424431&postcount=2) and comment the last 2 lines. I think that would do the trick.

---

### Post by theteju on 2012-12-27
Hey guys,

Thanks for prompt reply.

I really can not find which lines to comment out. 

This is whats happening upon running apt-get update. [http://pastebin.com/VmnVkDrs](http://pastebin.com/VmnVkDrs)

Let me know.

Thanks again.

---

### Post by plucky on 2012-12-27
> **theteju said:**
> Hey guys,

Thanks for prompt reply.

I really can not find which lines to comment out. 

This is whats happening upon running apt-get update. [http://pastebin.com/VmnVkDrs](http://pastebin.com/VmnVkDrs)

Let me know.

Thanks again.

Change your download server in **Software Sources** as the one you are using seems to be down.

Just tried your server in virtualbox and am getting the same error as you are.

Good Luck

---

### Post by theteju on 2012-12-30
Thank you.

That solved my problem. Could never guess it. I was just trying to keep main server less busy :P

Thanks much again. Peace.

---

### Post by BlinkinCat on 2012-12-30
To help others you could mark the thread as "solved" via Thread Tools at top of page.

---

