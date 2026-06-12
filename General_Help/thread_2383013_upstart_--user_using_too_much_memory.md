---
title: "upstart --user using too much memory"
date: 2018-01-19
forum: General Help
---

### Post by ardouronerous on 2018-01-19
Something strange happened to my computer about 6 hours ago.

My computer became unresponsive and my mouse became unresponsive as well, I could move it around but I'm unable to click on anything, but before things became too unresponsive, I managed to get into Task Manager and I see upstart --user was using about 3GB of memory.

Anyway, I managed to shutdown my PC and start it back again, and everything seems to be fine.  I'm running Xubuntu 16.04 LTS.

What could cause this? Is this a bug?

---

### Post by cruzer001 on 2018-01-20
Any reason your using upstart instead of systemd?

---

### Post by ardouronerous on 2018-01-20
I have systemd listed on Task Manager, it's listed as 'systemd/systemd --user'.

Are you saying I shouldn't have upstart installed in the first place? I never installed upstart.

---

### Post by vasa1 on 2018-01-20
What does```
ps axjf | grep -i upstart | grep -v "grep"
```show?

By the way, [What to do about upstart in ubuntu 16.04]("https://askubuntu.com/a/957088")

---

### Post by ardouronerous on 2018-01-20
```
 1136  1653  1653  1653 ?           -1 Ss    1000   0:00      \_ /sbin/upstart --user
 1653  1744  1742  1742 ?           -1 S     1000   0:00          \_ upstart-udev-bridge --daemon --user
 1653  1793  1791  1791 ?           -1 S     1000   0:00          \_ upstart-dbus-bridge --daemon --session --user --bus-name session
 1653  1794  1792  1792 ?           -1 S     1000   0:00          \_ upstart-dbus-bridge --daemon --system --user --bus-name system
 1653  1798  1797  1797 ?           -1 S     1000   0:00          \_ upstart-file-bridge --daemon --user
```

---

### Post by vasa1 on 2018-01-20
I'm on Kubuntu 16.04 (clean install) but the code I provided doesn't show anything related to upstart for me. So, the question is: what did you do to have upstart running on your system?

---

### Post by ardouronerous on 2018-01-20
I installed sox, so I could have a startup sound on my Xubuntu desktop.
Does sox install upstart as a dependency?

---

### Post by vasa1 on 2018-01-20
The link I provided clearly states that both upstart and systemd are present.

On my system, when I run *locate upstart*, I get:```
$ locate upstart
/etc/init/usb-modeswitch-upstart.conf
/etc/network/if-down.d/upstart
/etc/network/if-up.d/upstart
/lib/lsb/init-functions.d/01-upstart-lsb
/usr/share/upstart
/usr/share/doc/pulseaudio/examples/pulseaudio.upstart.example
/usr/share/indicator-application/upstart
/usr/share/indicator-application/upstart/xdg
/usr/share/indicator-application/upstart/xdg/autostart
/usr/share/indicator-application/upstart/xdg/autostart/indicator-application.desktop
/usr/share/locale-langpack/en@boldquot/LC_MESSAGES/upstart.mo
/usr/share/locale-langpack/en@quot/LC_MESSAGES/upstart.mo
/usr/share/locale-langpack/en_AU/LC_MESSAGES/upstart.mo
/usr/share/locale-langpack/en_CA/LC_MESSAGES/upstart.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/upstart.mo
/usr/share/upstart/sessions                                                                                                                          
/usr/share/upstart/xdg                                                                                                                               
/usr/share/upstart/sessions/at-spi2-registryd.conf                                                                                                   
/usr/share/upstart/sessions/dbus.conf                                                                                                                
/usr/share/upstart/sessions/gpg-agent.conf                                                                                                           
/usr/share/upstart/sessions/im-config.conf                                                                                                           
/usr/share/upstart/sessions/indicator-application.conf                                                                                               
/usr/share/upstart/sessions/no-pinentry-gnome3.conf                                                                                                  
/usr/share/upstart/sessions/session-migration.conf                                                                                                   
/usr/share/upstart/sessions/ssh-agent.conf                                                                                                           
/usr/share/upstart/xdg/autostart                                                                                                                     
/usr/share/upstart/xdg/autostart/at-spi-dbus-bus.desktop                                                                                             
/var/lib/app-info/icons/ubuntu-xenial-main/64x64/upstart-monitor_upstart-monitor.png                                                                 
/var/lib/app-info/icons/ubuntu-xenial-updates-main/64x64/upstart-monitor_upstart-monitor.png                                                         
$
```So upstart is present but not active in any way, AFAICT.

I don't know what *sox* needs. But it's interesting that the system of the poster of the AU question also had something to do with mythbuntu.

---

### Post by ardouronerous on 2018-01-20
is there a terminal command to call up sox's dependencies?

---

### Post by vasa1 on 2018-01-20
*apt depends sox* should do it.

---

### Post by ardouronerous on 2018-01-20
```
sox
 |Depends: libsox-fmt-alsa (= 14.4.1-5)
 |Depends: libsox-fmt-ao (= 14.4.1-5)
 |Depends: libsox-fmt-oss (= 14.4.1-5)
  Depends: libsox-fmt-pulse (= 14.4.1-5)
  Depends: libsox-fmt-base (= 14.4.1-5)
  Depends: libsox2 (= 14.4.1-5)
  Depends: libc6 (>= 2.15)
  Suggests: libsox-fmt-all
```

Doesn't seem to be dependant on upstart.

I don't know what I did to make it run.

Is it normal for upstart to use 3 gigs of memory?

---

### Post by vasa1 on 2018-01-20
Well, just be watchful the next time your RAM usage starts rising above comfort and then run```
top -bn1 -o %MEM | head -20
```and```
top -bn1 -o %CPU | head -20
```to get an idea of what else is running at the time upstart plays up.

Running```
ps axjf
``` at that time may not be a bad idea.

---

### Post by cruzer001 on 2018-01-20
At boot (grub) check advance options for switching between upstart and systemd.

---

