---
title: "Slow boot times since Ubunutu 18.04 install"
date: 2018-04-29
forum: General Help
---

### Post by TheNighthawk on 2018-04-29
Hi,

Since I have upgraded (reinstalled) my Del D630 laptop to Ubuntu 18.04 , boot times became "impossible". It literally takes many minutes just to get a login screen, and then still one minute or more to have working icons on a desktop. This for both X11 and Wayland sessions.

I ran the systemd analyse tools and I saw that the different snap and systemd services are causing a huge delay in booting. Anyone an idea how to overcome this or how to remove them without further breaking breaking my system?

koen@beite-m1:~$ systemd-analyze blame 
    1min 31.794s dev-loop8.device
    1min 31.790s dev-loop9.device
    1min 31.675s [EMAIL="systemd-backlight@backlight:intel_backlight.servic"]systemd-backlight@backlight:intel_backlight.servic[/EMAIL]e
    1min 31.144s systemd-rfkill.service
          1.408s dev-sda1.device
           822ms fwupd.service
           789ms dev-loop7.device
           689ms dev-loop6.device
           658ms dev-loop3.device
           634ms dev-loop1.device
           629ms dev-loop5.device
           626ms dev-loop0.device
           601ms dev-loop4.device
           562ms dev-loop2.device
           529ms networkd-dispatcher.service
           522ms systemd-udev-trigger.service
           491ms ModemManager.service
           490ms accounts-daemon.service
           437ms udisks2.service
           409ms NetworkManager.service



koen@beite-m1:~$ systemd-analyze critical-chain
The time after the unit is active or started is printed after the "@" character.
The time the unit takes to start is printed after the "+" character.

graphical.target @1min 33.705s
&#9492;&#9472;multi-user.target @1min 33.703s
  &#9492;&#9472;systemd-user-sessions.service @1min 33.620s +8ms
    &#9492;&#9472;network.target @1min 33.617s
      &#9492;&#9472;NetworkManager.service @1min 33.206s +409ms
        &#9492;&#9472;dbus.service @1min 33.119s
          &#9492;&#9472;basic.target @1min 32.981s
            &#9492;&#9472;sockets.target @1min 32.979s
              &#9492;&#9472;snapd.socket @1min 32.961s +15ms
                &#9492;&#9472;sysinit.target @1min 32.935s
                  &#9492;&#9472;apparmor.service @1min 32.710s +222ms
                    &#9492;&#9472;local-fs.target @1min 32.686s
                      &#9492;&#9472;home.mount @1.695s +22ms
                        &#9492;&#9472;systemd-fsck@dev-disk-by\x2duuid-79ea6e09\x2dcdf7\x2d4447\x2d9041\x2d6abffceb9e50.service @1.641s +47ms
                          &#9492;&#9472;dev-disk-by\x2duuid-79ea6e09\x2dcdf7\x2d4447\x2d9041\x2d6abffceb9e50.device @1.635s


Thanks for any help or tips,
br, Koen.

---

### Post by Autodave on 2018-04-29
Did you do a clean install or did you upgrade what you were using?  I rarely have any luck with upgrading: I just usually do a new install.

---

### Post by notter43 on 2018-04-29
I was a first time Ubuntu user starting with 17.10 on an older  Toshiba(Intel CPU w/Intel graphics).  It was fast and fairly stable  until the latest base update.  The next reboot after the update, the  normal light purple screen appeared but it never got to the login  screen.  The screen went blank and it sat there.  After many searches  and recovery attempts, I booted from an 18.04 LTS DVD, backed up my  files, and did a fresh install using 18.04.  So far, I am disappointed.   The time from power on to a useful system is far longer than 17.10  which was much shorter than the typical Windows system.  It also freezes  when opening things like Settings.  If I wait it out, it continues.  At  this point, I'm tempted to go back to 17.10 but I'll wait and see if  there are any solutions or updates to resolve this.

---

### Post by TheNighthawk on 2018-04-29
I may have found a work-around; my boot time got reduced from over 4  minutes back to about 50 seconds (Wayland session) by doing:
  
[LIST=1]
[*]sudo vi /etc/default/grub
[*]I changed the GRUB_CMDLINE_LINUX_DEFAULT boot parameter to:  GRUB_CMDLINE_LINUX_DEFAULT="video=SVIDEO-1:d"
[*]Save and exit vi
[*]sudo update-grub
[*]sudo reboot
[/LIST]
  br, Koen.

---

