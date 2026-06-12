---
title: "Ubuntu server suddenly got a gui"
date: 2020-05-25
forum: General Help
---

### Post by kulmanrenato on 2020-05-25
Hi,
I have a windows machine that has an ubuntu server (20.04) running in wmware player. I had my GPU undervolted to save some power, but i forgot to tell my gf to switch it back before playing.
The computer crashed and after i restarted the VM i found a gui login screen on the server. 
Its not like a desktop gui, its really minimal.
Its so minimal basically nothing runs in it, deluge runs, but a terminal doesnt. no software center etc.
I never seen this before, does anybody have an idea what could this be?

---

### Post by CelticWarrior on 2020-05-25
Yes, it looks like a very minimal Gnome desktop.

No, it doesn't suddenly appears out of nowhere. You or somebody else installed it.
No, it also has nothing to do with undervolting the GPU or crashes. It has to have been installed, period.

---

### Post by kulmanrenato on 2020-05-25
Thats a miracle for me,i did mess with the vm yesterday, but that was only a pihole install and uninstall and some tranmission settings and apt update & upgrade, but i am sure i did not mess with gnome.
I have absolutely no idea how that happened, but i managed to uninstall it. Thanks

---

### Post by deadflowr on 2020-05-25
> I have absolutely no idea how that happened,
Apt package management activity is logged so check out the log files in either 
/var/log/dpkg.log,
or 
/var/log/apt/history.log

/var/log/apt/history.log is probably better as it's just a quick digest of what was installed removed or other,
whereas /var/log/dpkg.log shows the whole process of what happened, so it can be tad bit tmi.

---

### Post by kulmanrenato on 2020-05-25
Why the hell i a never heard about this log file :D
I just checked the history log and what is interesting that i did not find anything gnome related in it in the last 10 day. Right now i dont have time to check the dpkg log file, but i think i am going to save it and dig into it tomorrow.
Thanks :)

---

### Post by ajgreeny on 2020-05-25
For future reference, a very useful command, which I have used occasionally in the past, to find what was installed and when is 
```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log
```
This will output a list arranged by date and time of every package installed.  I've used this in the past after installing a second DE to a system, then wanting to remove same second DE, not a simple job normally because of the  very many packages added when you install, for example, LXqt DE to a Xubuntu system.

You can, incidentally change the word install in that command to either remove or upgrade to show the list for those actions instead of installing packages.

---

### Post by shazbot-nz on 2020-07-03
I wondered the same thing, then realised I had copy & pasted instructions somewhere to install VirtualBox Guest additions;

```
apt install virtualbox-guest-dkms virtualbox-guest-x11
```
I'd say it's a safe bet virtualbox-guest-x11 installed X server as a dependency... oops  :evil:

---

