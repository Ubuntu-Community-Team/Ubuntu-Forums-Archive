---
title: "Cron-o-meter Help"
date: 2008-05-26
forum: General Help
---

### Post by zacw13 on 2008-05-26
I've been messing with this and I've searched for an answer, but still nothing is working. I'm using Ubuntu Hardy Heron currently.

I'm trying to install Cron-o-meter. [http://spaz.ca/cronometer/](http://spaz.ca/cronometer/)

I downloaded the OSX version, then unzipped it. Then I downloaded the Linux shell script. However, I have no idea where to go from there. The following are the instructions that are in the script:


# INSTRUCTIONS
#  1) Install Java 1.4 or later for Linux ([http://java.com/download/](http://java.com/download/))
#  2) Download Mac OS X Version and Unzip in desired location
#  3) Place this launcher script next to the application bundle 
#  4) Execute script to launch CRON-o-Meter


I have no idea what an application bundle is. If anyone can help me figure out this program, I would be grateful. Thanks.

---

### Post by kellemes on 2008-05-26
> **zacw13 said:**
> I've been messing with this and I've searched for an answer, but still nothing is working. I'm using Ubuntu Hardy Heron currently.

I'm trying to install Cron-o-meter. [http://spaz.ca/cronometer/](http://spaz.ca/cronometer/)

I downloaded the OSX version, then unzipped it. Then I downloaded the Linux shell script. However, I have no idea where to go from there. The following are the instructions that are in the script:


# INSTRUCTIONS
#  1) Install Java 1.4 or later for Linux ([http://java.com/download/](http://java.com/download/))
#  2) Download Mac OS X Version and Unzip in desired location
#  3) Place this launcher script next to the application bundle 
#  4) Execute script to launch CRON-o-Meter


I have no idea what an application bundle is. If anyone can help me figure out this program, I would be grateful. Thanks.

As I understand it..
- Unpack the OSX zip (this is your application bundle)
- Place your Linux shellscript (cronometer.sh) in the same directory as where the zip is unpacked.
- Issue the following commands from a terminal window..

Make the script executable..
```
sudo chmod +x cronometer.sh
```

Execute the script..
```
./cronometer.sh
```

---

### Post by zacw13 on 2008-05-26
I tried exactly as you told me and I got this:

~/.cron-o-meter$ ./cronometer.sh
bash: ./cronometer.sh: /bin/sh^M: bad interpreter: No such file or directory

---

### Post by zacw13 on 2008-05-28
Bump. I was working on it, but I still can't figure it out for the life of me. Right now, I had to resort to installing it on Windows through VirtualBox. Any help would be appreciated.

---

### Post by freedomtolearn on 2008-11-11
I have the same problem expect my error message looks like this:

me@xcompx:~$ sudo chmod +x cronometer.sh
sudo: unable to resolve host xcompx
chmod: cannot access `cronometer.sh': No such file or directory

---

