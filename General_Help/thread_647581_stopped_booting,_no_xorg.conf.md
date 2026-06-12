---
title: "stopped booting, no xorg.conf?"
date: 2007-12-22
forum: General Help
---

### Post by mrmustardman on 2007-12-22
my ubuntu stopped booting suddenly. when i boot into regular ubuntu, it says starting powernowd, then displayes random charactures in random places on my screen.

i boot into recovery mode, and it takes me to a command prompt. From here, i type xinit, and startx... either one gives me the error "fatal error: cannot read /etc/x11/xorg.conf" and takes me back to command prompt.

so i got curious and typed "nano /etc/x11/xorg.conf" and its empty. apperantly it cant even find /etc/x11...

but its odd, because all my other files are there, like my home folder and even all the contents of /etc,,, 

i have my ubuntu install cd on hand, so is there a way to replace xorg.conf from command prompt off the cd? or since im in liveubuntu now, perhaps i can just copy it from this to my harddrive some how?

thanks

---

### Post by me4oslav on 2007-12-22
have you tried:
```
dpkg-reconfigure xserver-xorg
```,as far as i know it should generate a new xorg.conf

---

### Post by taurus on 2007-12-22
It's /etc/[COLOR="Blue"]X[/COLOR]11/xorg.conf since Unix/Linux is CaSe SenSiTive.

---

### Post by mrmustardman on 2007-12-22
ok this is starting to scare me:
i tried the "dpkg-reconfigure xserver-xorg" command and gave me the following error:

```
Package 'xserver.org' is not installed and no info is available
use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents
/usr/sbin/dpkg-reconfigure: xserver.xorg is not installed.

```

this cant be good... is there anyway to get it from the repositorys? id probably have to connect to the internet, and also while your answering questions, what is the command (like nano and gedit = text editors) is the command line internet browser?

thanks\

---

### Post by me4oslav on 2007-12-22
well you have either not have your xserver-xorg installed,or you have wrong the command wrong.
make you you execute:
```
dpkg-reconfigure xserver-xorg
```,not dpkg-reconfigure xserver.xorg or dpkg-reconfigure xserver.org
If you doesn't server-xorg installed,just install it by typing:
```
apt-get install xserver-xorg
```

---

### Post by mrmustardman on 2007-12-22
this is getting heavy. 
i typed "apt-get install xserver-xorg"
and it told me it was already installed.

so i typed "apt-get remove xserver-xorg" and it uninstalled.

i then typed "apt-get install xserver-xorg" again, and it cant connect to any of the repositorys. i need to connect to the network first.z

i suck with networking on windows let alone unix command prompt... if someone could help me out with this, maybe i should start a new post on connecting with command prompt... you should know, my computer usually requires me to click on the network icon and select my router to connect.

this sucks... maybe i should just completely reinstall my OS, that would be hard knowing all my files are still here

---

### Post by me4oslav on 2007-12-22
if you have pppoe connection,you should be able to install it by typing:
```
pppoeconf
```,but i don't know is it gonna to start the connection after that.And BTW are you sure that you have written the reconfguration command for xserver-xorg wright,while you was still having it installed,bacause it should generate a brand new xorg.conf and fix your problems,because dpkg have returned the following erorr on your computer:
> Package 'xserver.org' is not installed and no info is available
/usr/sbin/dpkg-reconfigure: xserver.xorg is not installed.
Thats mean that you have tried to reconfigure either _xserver.org_,or _xserver.xorg_,not **xserver-xorg**
And i am out of time now it is 23.10 in Bulgaria now(this is where i live),so i am gonna  write you tomorrow,but i also think that the reinstallation is the best choice.

---

### Post by louieb on 2007-12-22
If your running Edgy, Feisty or Gutsy the package you want is xorg.
```
sudo apt-get install xorg 
```for Dapper its 
```
sudo aptitude install x-window-system-core
```If it tells you its already there then do a reinstall. That may work without an internet connection if the package is still in  the apt cache,  
More info here:
[Installation/LowMemorySystems - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Installation/LowMemorySystems")

Sorry did not notice the no internet. Try ```
sudo dhclient
```then```
 ifconfig 
```and see if you have an ip address.

---

### Post by mrmustardman on 2007-12-23
ok. got it working, finally. 
what i needed to do was connect to the interweb so i could re-download and reinstall xorg...
typed
dhclient
it looked for, and found, a connection...
typed 
apt-get install xorg
it connected, downloaded and installed it...

i rebooted, still didnt work, so i went back to recovery and typed
dpkg-reconfigure xserver-xorg (i think i did type it wrong the first time, and didnt need to reinstall xorg at all)
and it worked this time, i went through and reconfigured it, rebooted, and all my themes and files are still here.

thanks alot. :guitar:

---

