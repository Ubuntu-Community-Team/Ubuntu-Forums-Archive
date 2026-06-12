---
title: "VLC wont open"
date: 2019-05-13
forum: General Help
---

### Post by iamtheeggman2 on 2019-05-13
Hi

I am posting this thread yet again on the advice of a moderator.

I want to get vlc to work but it wont, here are issues:

Hi,

I wanted to use vlc and I still cant open it, ,  anyway, i opened vlc in terminal and it outputs this message  "Segmentation fault (core dumped)"

When i google this it sounds alarming here it says:

[https://www.geeksforgeeks.org/core-d...n-fault-c-cpp/]("https://www.geeksforgeeks.org/core-dump-segmentation-fault-c-cpp/")

"
Core Dump/Segmentation fault is a specific kind of error caused by accessing memory that “does not belong to you.”
 

[LIST]
[*]When a piece of code tries to do read and write  operation in a read  only location in memory or freed block of memory,  it is known as core  dump.
[*]It is an error indicating memory corruption."
[/LIST]



I checked the ram worked fine whn ei bought the computer, the sticks in  here have no errors. no other programe has this issue of opening and  then closing.

Where do i begin?

vlc -I skins2 brings it up for a moment but then it crashes the moment i click on it?


#I foudn this interesting article, but one of the resoluction commands didnt work for me


[https://forums.linuxmint.com/viewtopic.php?t=204481](https://forums.linuxmint.com/viewtopic.php?t=204481)

 	Code:
 	home@home-System-Product-Name:~$ sudo /usr/lib/vlc/vlc-cache-gen -f usr/lib/vlc/plugins
[sudo] password for home: 
sudo: /usr/lib/vlc/vlc-cache-gen: command not found
home@home-System-Product-Name:~$ 
Thanks in advance,

---

### Post by Rubi1200 on 2019-05-13
What version and desktop are you on?

Did you recently upgrade from one version to the next?

I know this sounds obvious but have you tried purging and reinstalling?

---

### Post by mc4man on 2019-05-13
Run this command, see if anything is returned. If so post.
```
cat .config/vlc/vlcrc |grep "avcodec-hw="
```

---

### Post by iamtheeggman2 on 2019-05-19
```
home@home-System-Product-Name:~$ cat .config/vlc/vlcrc |grep "avcodec-hw="
#avcodec-hw=any
home@home-System-Product-Name:~$ 


```

18.04 bionic lts
reinstall didnt help.
desktop in lubuntu lxde?

the window that pops up with the error report doesnt stay open when you click to view it , that window itself crashes.

---

### Post by cruzer001 on 2019-07-27
Is this a snap package?
```
snap info vlc
```
If so, remove it and install the deb package.

---

### Post by TheFu on 2019-07-27
> **iamtheeggman2 said:**
> no ideas then? :-(

Just a guess.

If the config files for VLC inside your HOME are owned by root, due to running with sudo, then when the normal userid is used, it might not have permissions to read/write stuff there.  Fix any permissions issues and don't run GUI programs with sudo.

---

