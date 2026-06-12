---
title: "Stuck in Terminal after Update"
date: 2013-03-19
forum: General Help
---

### Post by Danair81 on 2013-03-19
I just did the most recent update for 12.04.2 LTS 32bit on my Laptop. After the update finished it prompted me to restart. Upon restarting the computer it loads up to terminal, but won't load the GUI. how can I get the GUI to show up from terminal. Any help is appreciated.

---

### Post by Danair81 on 2013-03-19
I attempted all the step located here "[http://askubuntu.com/questions/168736/how-to-start-gui-from-command-line](http://askubuntu.com/questions/168736/how-to-start-gui-from-command-line)"  and still no success.

---

### Post by Danair81 on 2013-03-19
Would installing 12.10 write over the Operating system that is bad without destroying the existing documents that I have on the computer?

---

### Post by Bashing-om on 2013-03-19
Danair81; Rather than (re)installing, would you prefer to repair your present system ?

Prior to the updates were you using a proprietary graphics driver ? If so this driver may need to be rebuilt for the present configuration.[INDENT=2]
my small effort to help

[/INDENT]

---

### Post by Danair81 on 2013-03-19
I would love to just get my system back to working status. I think your right with the video card being the problem. I have tried a few things and I had the GUI working in Guest but couldn't log into my primary account. So I attempted to run the video card drivers I had before and it took a dump again. Below are the steps I took to get the computer to work in Guest account:

1) sudo apt-get install linux-source
2) sudo apt-get install linux
3) sudo apt-get autoremove nvidia-current
4) sudo apt-get install xserver-xorg xserver-xorg-video-all
5) sudo apt-add-repository ppa:noobslab/nvidia-quantal
6) sudo apt-get update
7) sudo apt-get install nvidia-current
8) sudo reboot

I think quantal is 12.10. I probably just need to find the correct technical term for 12.04 to get it to work properly.

---

### Post by Danair81 on 2013-03-19
Just did the following:

sudo apt-get --purge remove nvidia-*
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-settings
sudo reboot

I got to where I can use the Guest Account Again but the main user account still isn't working now. Any Ideas?

---

### Post by steeldriver on 2013-03-19
If the GUI works for your guest session then presumably there's nothing wrong with your graphics drivers - so check the ownership and permissions on the ~/.Xauthority file of you main account

```
ls -l /home/*username*/.Xauthority
```

If it's become owned by root rm (delete) it or chown it back to you

```
sudo chown *username*:*username* /home/*username*/.Xauthority
```

---

### Post by Danair81 on 2013-03-19
This is what it says after both of those commands in Guest Account:

guest-LR8kkI@linuxlaptop-laptop:~$ ls -l /home/linuxlaptop/.Xauthority
-rw------- 1 root root 63 Mar 19 09:19 /home/linuxlaptop/.Xauthority
guest-LR8kkI@linuxlaptop-laptop:~$ sudo chown linuxlaptop:linuxlaptop /home/linuxlaptop/.Xauthority
sudo: unable to change to sudoers gid: Operation not permitted
sudo: setresuid() [0, 0, 0] -> [122, -1, -1]: Operation not permitted

---

### Post by Danair81 on 2013-03-19
Nevermind I figured it out. I had to create another administrator account. Then use the commands you gave me. Thank you again you rock :D

---

### Post by Bashing-om on 2013-03-19
Danair81;
Couple of things to look at;
!st, let's see if we can rule out a graphics driver problem (guest account good indicates driver is good), but want to check:
Boot to grub menu, latest kernel highlighted, press "e" key for edit mode;
arrow down to line similar to this:"linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff" arrow across to the terms "quiet splash" and insert the term "text" -without the quotes- (if you want to also see scrolling boot messages delete the terms "quiet and splash"); <- This only effects this instance of booting.
ctl+x to continue the boot process -> text login; enter user name then password; Enter the terminal code:
```
 sudo service lightdm start
``` to start the graphical desktop.
key combo ctl+alt+f7 to change to this graphical desktop. Is it up and usable at this point ? Any errors printed to the screen ?
key combo ctl+alt+f1 to revert back to the tty1 console.
To shut down; terminal code:
```
sudo shutdown -h now
``` Reboot; replace "h" with "r".
Else there may exist a permissions issue with your home directory.
We will see. I think best one thing at a time.[INDENT=3]try'n to help

[/INDENT]

---

