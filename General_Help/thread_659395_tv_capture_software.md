---
title: "tv capture software"
date: 2008-01-05
forum: General Help
---

### Post by steve984 on 2008-01-05
is there any easy to use tv capture software for ubuntu, It took all day and I finally got my card to work but I need software to use it.  I tried mthtv and all get is the sam sql configure screen, why I need a sql to capture video is beyond me but I guess for people with complicated systems. anyways mythtv The mouse don't even work.  all I want is nice easy scan my channels click and record program that works.  any ideas thanks steve

---

### Post by uclalinux on 2008-01-05
To Watch TV there is  "KDEtv", and to record programs theres "kdvr"

Here is a some information I left for another guy about MythTV, I would really try to set up MythTV it will change how you watch TV. 
[http://ubuntuforums.org/showthread.php?t=650223](http://ubuntuforums.org/showthread.php?t=650223)

---

### Post by steve984 on 2008-01-06
I downloaded mythtv twice and both times it messed up my video display.  I got the card to work(kinda), and the only piece of the puzzle is the recording.  the one nice about ubuntu is I don't have to keep registering every time i reintall it if this was windows I already be making my phone calls.  is there a way to other linux software to work in this os or do I have stay in the repositories.  thanks for the suggestings steve

---

### Post by uclalinux on 2008-01-06
You can install softwear from source, this means that your computer will read and compile the softwere, it is alittle advance and can not alway run smoothly. The repositories should should hold everything you need, what you need to do is add extra ones, I curttly have about 23,000 programs I can insall in my repautors, here is what you need todo.   

copy this list 

```
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

##Universe

deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## Multiverse

deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Backports

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Canonical Partner Repository 

deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://packages.medibuntu.org/ gutsy free non-free
```

then in the terminal type ```
 sudo gedit /etc/apt/etc/apt/sources.list
```
delete all thats inthere and paste the new list, then save and close the file. 

then type this in the terminal ```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
``` 
then after it says ok 
type ```
sudo apt-get update

```

next time you goto the synaptic package manager you will have a ton of more programs to install. 

To install things from source it would be best to google how to install programs from source code, it is alittle more involve then just clicking an .exe file.  

Also if you can't find a program you want in the  synaptic package manager, google the program name and add .deb, a .deb is like an exe file for linux. If you ran the fedora linux, it would be called a rpm file.

---

