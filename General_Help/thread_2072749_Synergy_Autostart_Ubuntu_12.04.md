---
title: "Synergy Autostart Ubuntu 12.04"
date: 2012-10-18
forum: General Help
---

### Post by techborn on 2012-10-18
I am looking for help to get Quick Synergy to start directly after my system boots up. I have spent all last night looking up how to's and such but nothing worked, Ive tried adding it to the start up applications but that didnt work either. I would love some help with this as it is rather important to get working.


I should mention that my Ubuntu system is a client and not the server of Synergy.

Thanks in advance
Robert

---

### Post by ubtBaba on 2012-10-20
I have been having a real hard time getting quick synergy to work so I installed the new client/server on all my machines.

Then I found on another blog these instructions.

Source:[http://askubuntu.com/questions/15212/start-synergy-on-boot](http://askubuntu.com/questions/15212/start-synergy-on-boot)

For newer version of Ubuntu that use lightdm.

I have successfully done the following for running the synergy client for the login screen, and after I login. It is much simpler than the other answers, IMHO.

edit /etc/lightdm/lightdm.conf as root.

sudo vi /etc/lightdm/lightdm.conf
add the following line to the bottom of the file.

greeter-setup-script=/usr/bin/synergyc <ip/host>
restart lightdm. (it is better to do this from a terminal or ssh session)

sudo /etc/init.d/lightdm restart

---

### Post by ubtBaba on 2012-10-20
Also I prefer using nano so instead of 
sudo vi /etc/lightdm/lightdm.conf I used
sudo nano /etc/lightdm/lightdm.conf

I am still testing this out myself.

---

### Post by ubtBaba on 2012-10-20
So I have it working and I am pretty satisfied.  You mentioned the other HowTos, I had it working on previous versions and I saved those files to reuse but in Ubuntu 12.04, you are using Lightdm instead of GDM and the old howto's are written for GDM.

---

