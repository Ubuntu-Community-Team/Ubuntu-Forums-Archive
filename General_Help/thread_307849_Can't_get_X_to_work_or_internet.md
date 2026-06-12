---
title: "Can't get X to work or internet"
date: 2006-11-27
forum: General Help
---

### Post by Marc3090 on 2006-11-27
Please bear with me as I am somewhat new to using linux and especially the command line.

I upgraded my system and now the X server is not configured correctly so I cannot log into Gnome.  I can log into the command line though.  I found some advice on the net for using apt-get to repair it but I don't have net connectivity for some reason.  

Can someone tell me how to troubleshoot my internet connection by command line or put me to some good docs for that?

Is it possible to download a file onto a thumbdrive, from another computer, and then mount it and do the update from there? (I need to know how to mount a thumbdrive by command line)

The computer was working fine before the upgrade.  I am new to the command line so help must be basic.  Thank you anyone for your time.

Marc

---

### Post by Paul41 on 2006-11-27
You can try to run this to get X working. I don't think you have to be connected to the internet to run this.
```
sudo dpkg-reconfigure xserver-xorg
```

It will take you through a series of question on the setup. You can just select the default options on all of them, but select the nv video driver. Hopefully that will get you X server running again.

For the internet connection, can you ping sites?
```
ping google.com
```

---

