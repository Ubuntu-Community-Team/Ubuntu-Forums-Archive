---
title: "system-config-samba and gksu-properties crash on Lubuntu 14.10"
date: 2014-10-28
forum: General Help
---

### Post by stephen58 on 2014-10-28
I have installed a fresh, clean copy of Lubuntu 14.10 Trusty Tahr on an old Dell Precision M6400 laptop (32-bit). I installed wireless drivers for the Broadcom Corporation BCM4312 LP-PHY and got that working. I am now trying to get at least the folder /home/theUser/Public/ to be visible and accessible from the rest of the LAN Windows Homegroup. Looking around, it seems I need Samba, so I installed a bunch of stuff related to that. Part of the instructions say I should open the Samba system configuration window/GUI, but when I tried to do that it crashes immediately after I enter my password. While trying to troubleshoot that, I ran across a bit telling me to run "gsku properties" from the terminal, but that too crashes immediately after I enter my password. Poking around some, I see that [COLOR=#333333][FONT=UbuntuMono]/etc/samba/user[/FONT][/COLOR] has nothing in it.


[LIST]
[*]**Is there somewhere I can look to see what message flicks off the screen after I enter my password when trying to open the Samba system configuration GUI?**
[*]**Is there**** somewhere I can look to see why ****the Samba system configuration GUI does not open after I enter said password? Is it sensible to assume this failure indicates/implies it crashed?**
[*]**What else can I try to get it working? Is there any more information that could be useful for troubleshooting?**
[/LIST]

File sharing with Samba tutorials/documentation:
[http://ubuntuforums.org/showthread.php?t=1623346](http://ubuntuforums.org/showthread.php?t=1623346)
[http://captainbodgit.blogspot.com/2012/10/networking-with-lubuntu-win7-and.html](http://captainbodgit.blogspot.com/2012/10/networking-with-lubuntu-win7-and.html)
[http://ubuntuhandbook.org/index.php/2014/05/ubuntu1404-file-sharing-samba/](http://ubuntuhandbook.org/index.php/2014/05/ubuntu1404-file-sharing-samba/)
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)
[https://help.ubuntu.com/community/Samba/SambaServerGuide](https://help.ubuntu.com/community/Samba/SambaServerGuide)
[https://help.ubuntu.com/community/Samba/SambaClientGuide](https://help.ubuntu.com/community/Samba/SambaClientGuide)

Posts about troubleshooting system-config-samba:
[http://askubuntu.com/questions/289574/cannot-run-samba-interface-after-installing-13-04](http://askubuntu.com/questions/289574/cannot-run-samba-interface-after-installing-13-04)

Post about using gksu:
[http://askubuntu.com/questions/303818/samba-is-not-working-on-ubuntu-13-04/330597#330597](http://askubuntu.com/questions/303818/samba-is-not-working-on-ubuntu-13-04/330597#330597)

-- Thank you very much for your time and assistance.

---

### Post by mörgæs on 2014-10-29
Moving to General Help. You have a better chance here.

---

### Post by Morbius1 on 2014-10-29
Open a terminal and run:
```
gksu system-config-samba
```
If you get something like this as I just did on Ubuntu 14.10:
> self.basic_preferences_win = basicPreferencesWin.BasicPreferencesWin(self, self.xml, self.samba_data, self.samba_backend, self.main_window)
  File "/usr/share/system-config-samba/basicPreferencesWin.py", line 97, in __init__
    self.admin = libuser.admin()
SystemError: could not open configuration file `/etc/libuser.conf': No such file or directory
Create the missing file:
```
sudo touch /etc/libuser.conf
```
Then run this again:
```
gksu system-config-samba
```

It appears you may have other problem if you can't run "gksu properties" however so I don't know how much help this post will be to you.

I really don't know why they "release" these non LTS versions any more given their short life spans. They should thank the user who installs them for being part of the beta testing team.

---

### Post by stephen58 on 2014-10-29
@ [COLOR=#000000]Morbius1
That did it. Thanks![/COLOR]

---

