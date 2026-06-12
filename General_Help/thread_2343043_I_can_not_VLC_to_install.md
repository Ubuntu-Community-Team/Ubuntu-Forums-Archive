---
title: "I can not VLC to install?"
date: 2016-11-12
forum: General Help
---

### Post by Billisnice on 2016-11-12
$ sudo apt update
$ sudo apt upgrade
$ sudo apt install -f
$ sudo apt install vlc

billn@billn-N107:~$ sudo apt install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: vlc-nox (= 2.2.2-5) but 2.2.4-6~ubuntu16.04.1~ppa1 is to be installed
       Recommends: vlc-plugin-notify (= 2.2.2-5) but it is not going to be installed
       Recommends: vlc-plugin-samba (= 2.2.2-5) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
billn@billn-N107:~$

---

### Post by deadflowr on 2016-11-12
What ppa did you add?

---

### Post by Billisnice on 2016-11-12
Non that I am aware of...

---

### Post by ian-weisser on 2016-11-12
Please show us the complete output of:
```
ls /etc/apt/sources.list.d/
```

---

### Post by Billisnice on 2016-11-12
I got it to install but can NOT open DVD with it. I loaded restricted drivers and sudo apt-get install libdvdcss libdvdread4 libdvdnav4

Not sure where it come from but "Package 'libdvdcss2' is virtual."

---

### Post by oldos2er on 2016-11-12
On 16.04 or newer you need to run ```
sudo apt install libdvd-pkg

sudo dpkg-reconfigure libdvd-pkg
``` When the ncurses screen pops up use Tab to highlight "Ok" and press Enter. It will take a moment or two to install libdvdcss2.

---

### Post by Billisnice on 2016-11-12
Thanks, it works! how do i set up vlc to auto run when I insert a DVD?  Currently when i put in a DVD the puter does nothing after spinning a few times. No menus, etc. But I can run opening vlc.

---

### Post by deadflowr on 2016-11-12
Set the system to autorun DVDs and set vlc as the program to open them
Do so in System Settings >> Details >> Removable Media (don't check the never prompt and start option).
Set DVD video to vlc player.
And anytime you load a dvd it should auto start without any user intervention.

---

