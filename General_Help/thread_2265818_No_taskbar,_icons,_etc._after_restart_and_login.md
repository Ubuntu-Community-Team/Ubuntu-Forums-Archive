---
title: "No taskbar, icons, etc. after restart and login"
date: 2015-02-18
forum: General Help
---

### Post by Michelle_Hughson on 2015-02-18
Hello,

Today I installed some updates to my computer and restarted. After I logged back on, nothing seems to load. I am able to access tty1. 

My first instinct was to access grub and run recovery mode, since it has helped me in the past. None of the options helped. I have since been reading many forums and tried a variety of options that did not work. 

My system: Asus M5A97 R2.0 motherboard, AMD FX6300 processor, and a MSI Geforce GTX760 graphics card. I am running Ubuntu 14.04 LTS.

I will continue to post things that I try, to give a better idea of what my problem might be.

Thanks,
Michelle

---

### Post by Michelle_Hughson on 2015-02-18
Command: Sudo apt-get install unity
Result: ... Unity is already the newest version...

Command: sudo apt-get install --reinstall Ubuntu-desktop
No problems, reinstallation successful.

Command: sudo service lighdm restart
Result: lightdm stop/waiting
lightdm start/running, process 3400

I saw the following in the Ubuntu official documentation to disable compiz (I'm not sure what this is, or what it does):
Command: sudo chmod a-x /usr/bin/compiz
No result shown, and it didn't fix my problem.

---

### Post by JTCorlett on 2015-02-18
I know this probably a stupid answer to your difficult question but have you tried:

Command:sudo startx

---

### Post by nadarockyraccoon on 2015-02-18
Possibly lightdm is attempting to load the wrong session. Try:
```
cd /usr/share/xsessions/; ls
```
This will give you a list of available session, amongst which should be ubuntu.desktop
If it is listed (which it should be given your sudo apt-get install --reinstall ubuntu-desktop command), try:
```
sudo gedit /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
```
This file should contain atleast

[SeatDefaults]
user-session=ubuntu

If user-session=anything but ubuntu change it to ubuntu (this will load the unity desktop), if it is blank add the two lines above and save it and try logging in again.

it is possible to set user-session to other sessions than ubuntu, just drop the .desktop from the sessions listed for instance, my computer uses gnome-fallback.desktop, so user-session=gnome-fallback

---

### Post by Michelle_Hughson on 2015-02-26
Thanks for the suggestions!

I tried JTCorlett's suggestion of sudo startx and got the following message:

```
modprobe: FATAL: Module nvidia not found
```

I then restarted, and when I typed in my (correct) password, it just flickered back to the password screen. I installed updates (sudo apt-get update), upgrades (sudo apt-get upgrade), and restarted again, but same thing. 

Then I tried [COLOR=#000000]nadarockyraccoon's suggestion. Listing files and folders in xsessions showed "ubuntu desktop", as was expected, but when I coded: 

[/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]sudo gedit /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf[/FONT][/COLOR]
```

The result was:

```
error XDG_RUNTIME_DIR not set in the environment

(gedit:2290): Gtk-WARNING **: cannot open display
```

Thoughts anyone?

---

### Post by yancek on 2015-02-26
> modprobe: FATAL: Module nvidia not found

The above error message seem to sepcifically relate to your problem.  You could try the suggestions at either site below.

[http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/](http://www.binarytides.com/install-nvidia-drivers-ubuntu-14-04/)

[http://askubuntu.com/questions/451221/ubuntu-14-04-install-nvidia-driver](http://askubuntu.com/questions/451221/ubuntu-14-04-install-nvidia-driver)

---

