---
title: "Boot problem with Ubuntu, please help"
date: 2014-03-20
forum: General Help
---

### Post by M1ck4el on 2014-03-20
Hello,
I have big problems about my ubuntu : I can't boot it anymore.
I wanted to install kali linux & backtrack tools so I used that guide (shame on me...)
[http://www.youtube.com/watch?v=aOT8cB0r9cY](http://www.youtube.com/watch?v=aOT8cB0r9cY)

I followed 4 first steps :
I typed in my terminal:
sudo passwd root (and I changed the pwd)
sudo sh -c 'echo "greeter-show-manual-login=true" >> etc/lightdm/lightdm.conf'
sudo apt-get install gnome-sessio-fallback
sudo apt-get install gdebi && sudo apt-get install synpatic

I think the most important trouble is with that line 
sudo sh -c 'echo "greeter-show-manual-login=true" >> etc/lightdm/lightdm.conf'
Can you copy paste your file etc/lightdm/lightdm.conf please?
I can access the terminal with my (other) computer but i don't know what to do.

Thanks.

PS : I am quite new with Ubuntu so if u can explain a bit, thx.

---

### Post by dragonfly41 on 2014-03-20
If it helps you here is a copy of two default files in my /etc/lightdm (I haven't had need to change these from first installation on Ubuntu 12.04 32 bit)

lightdm.conf

```

[SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter

```

users.conf

```

#
# User accounts configuration
#
# NOTE: If you have AccountsService installed on your system, then LightDM will
# use this instead and these settings will be ignored
#
# minimum-uid = Minimum UID required to be shown in greeter
# hidden-users = Users that are not shown to the user
# hidden-shells = Shells that indicate a user cannot login
#
[UserAccounts]
minimum-uid=500
hidden-users=nobody nobody4 noaccess
hidden-shells=/bin/false /usr/sbin/nologin

```

---

### Post by Impavidus on 2014-03-20
The only thing that command did was appending the line **greeter-show-manual-login=true** to the file etc/lightdm/lightdm.conf. Assuming you were in the root directory when you gave that command, it was added to the file that by default has the contents posted by dragonfly41. (If you were somewhere else a new file was created, which will most likely be ignored.)

---

### Post by grahammechanical on 2014-03-20
Please explain what "I can't boot it any more" means. How far does it get in the boot process? Where does the process stop? Please describe what you see on the screen.

I may be ignorant in many things but I cannot see anything in those 4 commands that would stop the boot menu from loading, or stop the boot menu from loading Linux, or stop Linux from loading LightDM and LightDM in turn loading a login screen and the login screen from loading the desktop environment or the desktop environment from loading a user interface.

I also fail to see why those commands are necessary in order to do what you wanted. Why change the password? Yes we need manual login to select an alternative desktop environment but why need a gnome-session-fallback?

Regards.

---

