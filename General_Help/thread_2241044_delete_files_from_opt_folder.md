---
title: "delete files from opt folder"
date: 2014-08-23
forum: General Help
---

### Post by harlie on 2014-08-23
I have a program called allvideodownloader  I downloaded and installed it from the software center. It does not work and software center can not remove it. I found it is in the opt folder along with google earth folder and files. I need to find out how to remove allvideo and not the google earth folder. I tried    "sudo apt-get remove allvideodownloader" but it does not remove it. I found that permission is denied because it says I am not the owner. Im the owner of the computer and root user.
So how can I get rid of this monster? Thanks for any help.
harlie:mad:

---

### Post by ibjsb4 on 2014-08-24
[https://apps.ubuntu.com/cat/applications/allvideodownloader/](https://apps.ubuntu.com/cat/applications/allvideodownloader/)

Im not finding this package in my repositories.  Must be some third party magic going on when installing this package with the software center.  Try this:
```
sudo dpkg -r allvideodownloader
```
And then clean things up with autoclean and autoremove.

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

You also may want to look into using SPM for installing, removing and cleaning.  IMO it works better than the software center.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

---

### Post by harlie on 2014-08-24
Thanks I hope this works, can't get to it till this pm, but I will give it a shot then.
harlie

---

### Post by ibjsb4 on 2014-08-24
Just take the time to read whats going on, that should keep you out of trouble :)

---

### Post by harlie on 2014-08-24
Hi;
I entered this command and the return was    "dpkg: warning: ignoring request to remove allvideodownloader which isn't installed"  that possibly may be due to my trying to remove it from the software center. "uninstall"
should I chance doing a reinstall from the software center? 
the progran is there for sure it is taking 89+ MB.
thanks
harlie

---

### Post by ibjsb4 on 2014-08-24
If it was me, I just manually remove it.

```
gksudo nautilus
```

Then do a "filesystem" search for allvideodownloader and remove.  Just have a care, the safety is off and anything you remove is gone forever.

---

### Post by harlie on 2014-08-25
Thank you. This got rid of the thing I don't know what it means but after moving the thing to trash and closing the search window the following message was shown                 (nautilus:2392): GLib-critical **: source ID 107 was not found when attempting to remove it. But a check shows the thing is not there now. Again thanks.
harlie

---

