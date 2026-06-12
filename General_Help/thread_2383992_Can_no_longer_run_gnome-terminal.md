---
title: "Can no longer run gnome-terminal"
date: 2018-02-01
forum: General Help
---

### Post by goodstuff9 on 2018-02-01
Ubuntu 17.10 (xorg), gnome 3.26.2.  

I suddenly began having this problem when I try to run gnome-terminal, I can't figure out what caused this:  


main19@system19:~$ gnome-terminal
Error constructing proxy for org.gnome.Terminal:/org/gnome/Terminal/Factory0: Error calling StartServiceByName for org.gnome.Terminal: Timeout was reached
main19@system19:~$ 

This causes gnome--terminal not to start.  

I have tried looking online, everyone says it is a locale problem, here is my locale output:  


main19@system19:~$ locale
LANG=en_US.UTF-8
LANGUAGE=
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
main19@system19:~$ 


I have run out of ideas, if anyone can provide help with this that would be great.

---

### Post by cruzer001 on 2018-02-02
> Error constructing proxy

I haven't seen that one in the terminal.  Have you tried purging and reinstalling?

```
sudo apt purge gnome-terminal

rm ~/.config/gnome-terminal

sudo apt install gnome-terminal
```

---

### Post by goodstuff9 on 2018-02-02
> **cruzer001 said:**
> I haven't seen that one in the terminal.  Have you tried purging and reinstalling?

```
sudo apt purge gnome-terminal

rm ~/.config/gnome-terminal

sudo apt install gnome-terminal
```

I have  done that.....  no improvement, still the exact same problem.

---

### Post by cruzer001 on 2018-02-02
Like you, my searches point to locale being the problem.

[https://ubuntuforums.org/showthread.php?t=2295530](https://ubuntuforums.org/showthread.php?t=2295530)

---

### Post by litlesam on 2018-02-02
Have you tried login as a guest and trying the terminal?

---

### Post by vasa1 on 2018-02-02
Could you make keyboard shortcuts with```
LANG=C gnome-terminal
```or```
LANG=POSIX gnome-terminal
```and give them a try?

---

### Post by goodstuff9 on 2018-02-02
> **vasa1 said:**
> Could you make keyboard shortcuts with```
LANG=C gnome-terminal
```or```
LANG=POSIX gnome-terminal
```and give them a try?

I am sorry to say this, but....  I don't know what you're asking me to do.  "Keyboard shortcuts" are what exactly?

---

### Post by goodstuff9 on 2018-02-03
I ended up refreshing my HOME directory, that solved this problem.

---

### Post by vectorphresh on 2018-09-15
> **goodstuff9 said:**
> Ubuntu 17.10 (xorg), gnome 3.26.2.  

I suddenly began having this problem when I try to run gnome-terminal, I can't figure out what caused this:  


main19@system19:~$ gnome-terminal
Error constructing proxy for org.gnome.Terminal:/org/gnome/Terminal/Factory0: Error calling StartServiceByName for org.gnome.Terminal: Timeout was reached
main19@system19:~$ 

This causes gnome--terminal not to start.  

I have tried looking online, everyone says it is a locale problem, here is my locale output:  


main19@system19:~$ locale
LANG=en_US.UTF-8
LANGUAGE=
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=
main19@system19:~$ 


I have run out of ideas, if anyone can provide help with this that would be great.

In case anyone finds this thread in the future, on 18.04 I had this issue until I uninstalled Chrome Remote Desktop. I couldn't get it to play nice with GNOME 3, and forgot I installed the package. Try removing it and see if that helps.
```
$ sudo apt remove chrome-remote-desktop
```

---

### Post by 1-shane on 2018-12-28
> **vectorphresh said:**
> In case anyone finds this thread in the future, on 18.04 I had this issue until I uninstalled Chrome Remote Desktop. I couldn't get it to play nice with GNOME 3, and forgot I installed the package. Try removing it and see if that helps.
```
$ sudo apt remove chrome-remote-desktop
```


BINGO!  That was indeed the problem.  Thanks!

---

