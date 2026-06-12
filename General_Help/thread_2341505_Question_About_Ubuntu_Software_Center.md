---
title: "Question About Ubuntu Software Center"
date: 2016-10-28
forum: General Help
---

### Post by shane_faulkinbury2 on 2016-10-28
I installed Ubuntu 16.10 LTS a couple of days ago.  I was installing all my programs I had on 16.04.  However some of them ask me to enter my credentials I use to log on to this site.  I wonder why it's doing that now?  Oh yeah, when I enter the credentials and hit okay it brings me to this site instead of installing the program.  The first program it did this on was VLC Media Player.  What could be wrong?

---

### Post by Frogs Hair on 2016-10-28
It looks like VLC has switched to the "snap" package format so try the following command.  The snap commands I tried fail to install VLC despite much activity in the terminal . 

```
sudo apt-get install vlc
```

Ubuntu Soft ware is a work in progress so the synaptic package manger may be a better option. 

Info: [https://insights.ubuntu.com/2016/06/14/universal-snap-packages-launch-on-multiple-linux-distros/](https://insights.ubuntu.com/2016/06/14/universal-snap-packages-launch-on-multiple-linux-distros/)

---

### Post by howefield on 2016-10-29
Clicking on that particular VLC icon in Ubuntu Software will show that it originates from the snappy store and unfortunately installing snaps from Ubuntu Software is not yet without issue. It is best to install snaps from the terminal in the meantime.. firstly by logging in to SSO and then issuing the install command, eg

```
sudo snap login xxxxxxxxx@xxxxxx.com
[sudo] password for hugh: 
Password: 
Login successful
hugh@yakkety:~$ snap install vlc
vlc (stable) daily from 'videolan' installed
```

However there are limitations to using the snapped version of VLC that probably mean that isn't the package you really want, as Frogs Hair suggests you can install the apt package via the command line if you don't see it in the Ubuntu Software application.

---

### Post by shane_faulkinbury2 on 2016-10-29
Thanks guys!  I installed VLC from my terminal last night.  I will try out Synaptic today.

---

