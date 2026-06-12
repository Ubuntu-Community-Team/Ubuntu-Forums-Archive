---
title: "GDebi &amp; Synaptic Package Manager won't open on 17.10"
date: 2017-12-16
forum: General Help
---

### Post by David4321 on 2017-12-16
Just installed 17.10. GDebi & Synaptic Package Manager appear to install correctly, but will not open. Can't check for dependencies (that's why I'm trying to install them :))

All other software installing fine.


Any suggestions?

---

### Post by jeremy31 on 2017-12-16
In terminal try ```
xhost +si:localuser:root
```
Then try gdebi or synaptic.  This is because of a limitation of elevated privileges on GUI programs in Wayland

---

### Post by David4321 on 2017-12-18
Thank you, this worked. Does this change expose my OS to any elevated risk?

Also, this does not seem to persist after restart. How can I make a permanent change to allow opening Gdebi & Synaptic. Another affected program is Gparted. Thanks.

---

### Post by David4321 on 2017-12-19
No, something different is going on with GDebi. Synaptic & Gparted are opening fine, I've never yet gotten GDebi to open. I've installed and uninstalled multiple times, using Ubuntu Software Center app. When installed, it does not show up in Applications list, or in list of available applications to associate for opening .deb files, nor in list of Installed applications in Software Center. However, it can be searched in Software Center from the All tab, and when found it is marked as installed. But when the Launch button on it's page is clicked, nothing happens. It can be uninstalled and reinstalled, but there is no change.

---

### Post by #&amp;thj^% on 2017-12-19
When calling gdebi in wayland try this:
```
sudo gdebi-gtk 
```
After you have run the code jeremey31 has provided. (xhost +si:localuser:root)
Be aware this will only last the current logedin session, I made a alias in my .bashrc for such needs.

---

### Post by David4321 on 2017-12-19
Result is: "sudo: gdebi-gtk: command not found"

I don't actually know what wayland or .bashrc are. I never had this problem in 16.04, all applications including elevated always opened straight away from icons, perhaps with password prompt dialog when needed. I'm looking for safe steps to make permanent changes to restore this functionality in 17.10. Thanks.

---

### Post by #&amp;thj^% on 2017-12-19
Welcome to Wayland Session then.:) ...Your right that you have not seen this on 16.04 but wayland is the new replacement for X11/xorg
Can you show me this then?
```
apt policy gdebi
```

---

### Post by David4321 on 2017-12-21
Ha, thanks! It's a good thing I don't know what X11/xorg was, or I might miss it... ;)

Result is this:
"~$ apt policy gdebigdebi:
  Installed: (none)
  Candidate: 0.9.5.7+nmu1ubuntu3
  Version table:
     0.9.5.7+nmu1ubuntu3 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful/universe amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful/universe i386 Packages"

---

### Post by #&amp;thj^% on 2017-12-21
> **David4321 said:**
> Ha, thanks! It's a good thing I don't know what X11/xorg was, or I might miss it... ;)

Result is this:
"~$ apt policy gdebigdebi:
  Installed: (none)
  Candidate: 0.9.5.7+nmu1ubuntu3
  Version table:
     0.9.5.7+nmu1ubuntu3 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful/universe amd64 Packages
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) artful/universe i386 Packages"

Instead of your output **"apt policy gdebigdebi:"**
Use this exactly
```
apt policy gdebi
```
That shows not installed.

---

### Post by David4321 on 2017-12-21
Ah, result is identical. I didn't type gdebi twice, second instance was part of system reply, was just missing a carriage return that didn't copy from terminal.

---

### Post by #&amp;thj^% on 2017-12-21
I kind of thought that, just had to be sure.
So we now know why we got "Result is: "sudo: gdebi-gtk: command not found""  
Because not installed. Right? ;)

---

### Post by David4321 on 2017-12-27
I managed to install GDebi via terminal. 

Fix does not persist. I must enter '[COLOR=#000000][FONT=&quot]xhost +si:localuser:root'[/FONT][/COLOR] in terminal after every restart, or elevated permission applications will not open.

I'm looking for a persistent fix to allow Wayland to call elevated permission applications, with only password prompt dialogue, as in 16.04 and earlier.

Thanks.

---

### Post by #&amp;thj^% on 2017-12-27
They are working on things right now to fix this for some apps.
until then you will just have to accept that's the way it is on wayland.
If you want I can show you how to shorten that with your .bashrc file.
**But Note this will Always last for just the Current Session!**

---

### Post by cariboo on 2017-12-28
There is a possible solution [here]("https://ubuntuforums.org/showthread.php?t=2375077&p=13701916&viewfull=1#post13701916"). I haven't tried it myself.

---

### Post by kurt18947 on 2017-12-29
I use Synaptic and have the same issue with 17.10 and Wayland. I have created at least 2 accounts, the default account with sudo privileges and one other desktop account. It is possible to select either Xorg or Wayland as the display manager for that session. I have the sudo account set to use X which will open Synaptic normally and the desktop account using Wayland. This isn't a perfect solution but user switching seems to work well in 17.10 so I don't find it too onerous.

---

### Post by David4321 on 2017-12-31
> **1fallen said:**
> They are working on things right now to fix this for some apps.
until then you will just have to accept that's the way it is on wayland.
If you want I can show you how to shorten that with your .bashrc file.
**But Note this will Always last for just the Current Session!**

Understood, thank you. I look forward to a method for these permissions that persists.

---

