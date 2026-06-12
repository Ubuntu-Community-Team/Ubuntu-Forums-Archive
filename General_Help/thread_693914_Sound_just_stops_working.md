---
title: "Sound just stops working"
date: 2008-02-11
forum: General Help
---

### Post by dethredic on 2008-02-11
I am having this problem, that started about a week ago. At first it didn't happen often, but now it happens a lot.

I will be surfing the web, IMing, watching video listening to music etc, when all of a sudden my sound just stops working. I don't ever remember the sound not working while I was in the middle of something, but like when the next song starts it just has no sound. 

The only clues I can gather from what is going on is when amarok is open, and I press play I get and error: 
> Audio output unavailable; the device is busy.

xine parameters:

This sound stops working sometimes when I don't have Amarok running, but that is the first time I saw the error.

I fix this problem by restarting X, but it usually it happens again.

Is there a fix for this?

---

### Post by apetresc on 2008-02-11
This is a well-known problem; it's caused by some (usually old) applications accessing the sound card directly instead of through the mixer. There's no fix for this except for fixing the application itself. Usually when this happens to me I close sound-producing applications one-by-one until I find out which one caused the problem (sound will work again as soon as you close the offending program).

I use the System->Preferences->Sound->Test to test after each close if it's working again.

Hope this helps.

---

### Post by dethredic on 2008-02-11
I can't seem to find the application that is doing this.

I have closed all the things that I have opened (Firefox / Pidgin)

and in the system monitor there are many process running, but none seem like a sound using program.
Here are the process I have running
> 
bonobo-activation-server
compiz
compiz.real
dbus-daemon
gcconfd-2
gedit
gnome-keyring-daemon
gnome-panel
gnome-power-manager
gnome-screenserver
gnome-settings-daemon
gnome-system-monitor
gnome-vsf-daemon
gnome-volume-manager
gtk-window-decorator
gweather-applet-2
imwheel
mapping-daemon
nautilus
run-mozilla.sh
ssh-agent
trackerd
trasapplet
update-notifier
vino-session
x-session-manager

I don't know which ones I should kill. There are many more that do not have their own icon.
I will just see what other ones are running when my sound stops.

---

### Post by dethredic on 2008-02-11
Well, it just happened again. and I don't see any thing that is causing the problem.

EDIT: there are no processes that are running that are not there at startup when my sound is working.

---

### Post by MighMoS on 2008-02-11
Including a complete ps ax -H may be helpful, but some things that come to mind are firefox. Flash has given me issues with stealing the sound. Another common culprit / culprits are esd and pulseaudio -- both are sound servers which can forget to give back the hardware at time. ```
killall esd
``` or ```
killall pulseaudio
``` may help next time it happens.

If neither of those helps you could try ```
lsof |grep /dev
``` which will show every program accessing some device, Your sound will be /dev/dsp or under /dev/snd.

---

### Post by roschern on 2008-02-12
I have also had this problem.

Displaying which apps using the sound device reveals that soffice (Open Office) is stealing my sound device. Closing OOo solved the problem.

---

### Post by dethredic on 2008-02-13
Here is my ps ax -H (taken from when my sound was not working)

> 
 PID TTY      STAT   TIME COMMAND
    2 ?        S<     0:00 [kthreadd]
    3 ?        S<     0:00   [migration/0]
    4 ?        SN     0:00   [ksoftirqd/0]
    5 ?        S<     0:00   [watchdog/0]
    6 ?        S<     0:00   [migration/1]
    7 ?        SN     0:00   [ksoftirqd/1]
    8 ?        S<     0:00   [watchdog/1]
    9 ?        S<     0:00   [events/0]
   10 ?        S<     0:00   [events/1]
   11 ?        S<     0:00   [khelper]
   31 ?        S<     0:00   [kblockd/0]
   32 ?        S<     0:00   [kblockd/1]
   33 ?        S<     0:00   [kacpid]
   34 ?        S<     0:00   [kacpi_notify]
  191 ?        S<     0:00   [kseriod]
  220 ?        S<     0:02   [kswapd0]
  271 ?        S<     0:00   [aio/0]
  272 ?        S<     0:00   [aio/1]
 2209 ?        S<     0:00   [ksuspend_usbd]
 2210 ?        S<     0:00   [khubd]
 2235 ?        S<     0:00   [ata/0]
 2236 ?        S<     0:00   [ata/1]
 2237 ?        S<     0:00   [ata_aux]
 2249 ?        S<     0:00   [khpsbpkt]
 2361 ?        S<     0:00   [knodemgrd_0]
 2364 ?        S<     0:00   [scsi_eh_0]
 2365 ?        S<     0:00   [scsi_eh_1]
 2473 ?        S<     0:00   [scsi_eh_2]
 2474 ?        S<     0:00   [scsi_eh_3]
 2495 ?        S<     0:00   [scsi_eh_4]
 2496 ?        S<     0:00   [scsi_eh_5]
 2652 ?        S<     0:00   [kjournald]
 3979 ?        S<     0:00   [kpsmoused]
 4552 ?        S<     0:02   [kjournald]
 5057 ?        S<     0:00   [kondemand/0]
 5058 ?        S<     0:00   [kondemand/1]
32721 ?        S      0:00   [pdflush]
32722 ?        S      0:00   [pdflush]
    1 ?        Ss     0:01 /sbin/init
 2860 ?        S<s    0:00   /sbin/udevd --daemon
 4555 ?        Ss     0:00   /sbin/mount.ntfs /dev/sda1 /media/sda1 -o rw,umask=
 4822 tty4     Ss+    0:00   /sbin/getty 38400 tty4
 4823 tty5     Ss+    0:00   /sbin/getty 38400 tty5
 4825 tty2     Ss+    0:00   /sbin/getty 38400 tty2
 4827 tty3     Ss+    0:00   /sbin/getty 38400 tty3
 4829 tty1     Ss+    0:00   /sbin/getty 38400 tty1
 4830 tty6     Ss+    0:00   /sbin/getty 38400 tty6
 5016 ?        Ss     0:00   /usr/sbin/acpid -c /etc/acpi/events -s /var/run/acp
 5138 ?        Ss     0:00   /sbin/syslogd -u syslog
 5191 ?        S      0:00   /bin/dd bs 1 if /proc/kmsg of /var/run/klogd/kmsg
 5193 ?        Ss     0:00   /sbin/klogd -P /var/run/klogd/kmsg
 5214 ?        Ss     0:00   /usr/bin/dbus-daemon --system
 5230 ?        Ssl    0:00   /usr/sbin/NetworkManager --pid-file /var/run/Networ
 5244 ?        Ss     0:00   /usr/sbin/NetworkManagerDispatcher --pid-file /var/
 5257 ?        Ss     0:00   /usr/bin/system-tools-backends
 5258 ?        S      0:00     dbus-daemon --session --print-address --nofork
 5277 ?        Ss     0:00   /usr/sbin/hald
 5278 ?        S      0:00     hald-runner
 5363 ?        S      0:00       hald-addon-keyboard: listening on /dev/input/ev
 5390 ?        S      0:00       hald-addon-keyboard: listening on /dev/input/ev
 5394 ?        S      0:00       hald-addon-keyboard: listening on /dev/input/ev
 5399 ?        S      0:00       hald-addon-keyboard: listening on /dev/input/ev
 5483 ?        S      0:00       hald-addon-acpi: listening on acpid socket /var
 5561 ?        S      0:05       hald-addon-storage: polling /dev/hda (every 2 s
 5683 ?        S      0:00       hald-addon-keyboard: listening on /dev/input/ev
 6104 ?        S      0:00       hald-addon-keyboard: listening on /dev/input/ev
 5403 ?        Ssl    0:00   /usr/sbin/console-kit-daemon
 5496 ?        Ss     0:00   avahi-daemon: running [phil.local]
 5497 ?        Ss     0:00     avahi-daemon: chroot helper
 5515 ?        Ss     0:00   /usr/sbin/dhcdbd --system
 5800 ?        S      0:00     /sbin/dhclient -1 -lf /var/lib/dhcp3/dhclient.eth
 5570 ?        Ss     0:00   /usr/sbin/gdm
 5573 ?        S      0:00     /usr/sbin/gdm
 5576 tty7     SLs+  43:59       /usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:
 5892 ?        Ssl    0:00       x-session-manager
 5934 ?        Ss     0:00         /usr/bin/ssh-agent x-session-manager
 5948 ?        S      0:00         /bin/sh /usr/bin/compiz --sm-client-id defaul
 6048 ?        S      0:19           /usr/bin/gtk-window-decorator --replace
 6049 ?        SL    16:32           /usr/bin/compiz.real --ignore-desktop-hints
 5951 ?        S      0:19         gnome-panel --sm-client-id default1
 5954 ?        S      0:55         nautilus --no-default-window --sm-client-id d
 6051 ?        S      0:00         vino-session --sm-client-id default5
 6059 ?        S      0:00         update-notifier
 6065 ?        SNl    0:02         trackerd
 5631 ?        Ss     0:15   /usr/sbin/btnx -b
 5684 ?        Ss     0:00   /usr/sbin/atd
 5698 ?        Ss     0:00   /usr/sbin/cron
 5889 ?        SL     0:00   /usr/bin/gnome-keyring-daemon -d
 5929 ?        Ss     0:04   /usr/bin/imwheel 
 5936 ?        S      0:00   /usr/lib/libgconf2-4/gconfd-2 6
 5940 ?        Ss     0:00   dbus-daemon --fork --print-address 17 --print-pid 1
 5942 ?        Sl     0:06   /usr/lib/gnome-control-center/gnome-settings-daemon
 5958 ?        Ss     0:00   gnome-volume-manager --sm-client-id default4
 5963 ?        Ssl    0:00   /usr/lib/bonobo-activation/bonobo-activation-server
 6009 ?        S      0:00   /usr/lib/gnome-vfs-2.0/gnome-vfs-daemon
 6069 ?        Ss     1:32   gnome-screensaver
 6071 ?        S      0:00   /usr/lib/nautilus-cd-burner/mapping-daemon
 6089 ?        Ssl    0:02   /usr/sbin/g15daemon
 6091 ?        Ss     0:00   gnome-power-manager
 6129 ?        S      0:00   /usr/lib/gnome-applets/trashapplet --oaf-activate-i
 6179 ?        S      0:00   /usr/lib/gnome-applets/gweather-applet-2 --oaf-acti
 6184 ?        Sl     1:02   pidgin
 6364 ?        S      0:02   /usr/lib/notification-daemon/notification-daemon
 6752 ?        Sl     4:22   amarokapp
 6781 ?        S      0:00     ruby /usr/share/apps/amarok/scripts/score_default
 7977 ?        Sl     0:06     /usr/bin/perl -w /home/phil/.kde/share/apps/amaro
 7980 ?        Sl     0:02       g15composer /home/phil/.g15amaroklcdpipe
 6755 ?        Ss     0:00   kdeinit Running...        
 6761 ?        S      0:02     klauncher [kdeinit]       
29847 ?        S      0:00     kio_file [kdeinit] file   
 6758 ?        S      0:12   dcopserver [kdeinit] --n  
 7471 ?        S      0:00   /bin/sh /usr/bin/firefox
 7483 ?        S      0:00     /bin/sh /usr/lib/firefox/run-mozilla.sh /usr/lib/
 7487 ?        Sl    29:57       /usr/lib/firefox/firefox-bin
11301 ?        S      0:01   kget [http://rapidshare.com/files/68229052/sharpnose](http://rapidshare.com/files/68229052/sharpnose)
11328 ?        S      0:00   knotify [kdeinit]         
11433 ?        S      0:00   kio_uiserver [kdeinit]    
  492 ?        Sl     0:04   gimp file:///home/phil/Desktop/Screenshot.png
  495 ?        S      0:00     /usr/lib/gimp/2.0/plug-ins/script-fu -gimp 9 8 -r
  599 ?        Sl     0:00   gnome-terminal
  601 ?        S      0:00     gnome-pty-helper
  602 pts/0    Ss     0:00     bash
  619 pts/0    S      0:00       su
  620 pts/0    S      0:00         bash
  631 pts/0    R+     0:00           ps ax -H



The first two command did not work (I didn't have the processes running), and the third gave me this list: (again from when my sound wasn't working)
> 
phil@phil:~$ lsof |grep /dev
gnome-ter   668       phil    0r      CHR        1,3              9209 /dev/null
gnome-ter   668       phil   16u      CHR        5,2              4337 /dev/ptmx
bash        672       phil    0u      CHR      136,0                 2 /dev/pts/0
bash        672       phil    1u      CHR      136,0                 2 /dev/pts/0
bash        672       phil    2u      CHR      136,0                 2 /dev/pts/0
bash        672       phil  255u      CHR      136,0                 2 /dev/pts/0
lsof        753       phil    0u      CHR      136,0                 2 /dev/pts/0
lsof        753       phil    2u      CHR      136,0                 2 /dev/pts/0
grep        754       phil    1u      CHR      136,0                 2 /dev/pts/0
grep        754       phil    2u      CHR      136,0                 2 /dev/pts/0
gnome-key  5889       phil    0r      CHR        1,3              9209 /dev/null
gnome-key  5889       phil    1w      CHR        1,3              9209 /dev/null
gnome-key  5889       phil    2w      CHR        1,3              9209 /dev/null
gnome-key  5889       phil    6w      CHR        5,1              9202 /dev/console
x-session  5892       phil    0r      CHR        1,3              9209 /dev/null
imwheel    5929       phil    0r      CHR        1,3              9209 /dev/null
gconfd-2   5936       phil    0u      CHR        1,3              9209 /dev/null
gconfd-2   5936       phil    1u      CHR        1,3              9209 /dev/null
gconfd-2   5936       phil    2u      CHR        1,3              9209 /dev/null
gconfd-2   5936       phil    3u      CHR        1,3              9209 /dev/null
dbus-daem  5940       phil    0u      CHR        1,3              9209 /dev/null
dbus-daem  5940       phil    1u      CHR        1,3              9209 /dev/null
dbus-daem  5940       phil    2u      CHR        1,3              9209 /dev/null
dbus-daem  5940       phil    4u      CHR        1,3              9209 /dev/null
gnome-set  5942       phil    0u      CHR        1,3              9209 /dev/null
gnome-set  5942       phil    1u      CHR        1,3              9209 /dev/null
gnome-set  5942       phil    2u      CHR        1,3              9209 /dev/null
gnome-set  5942       phil    4u      CHR        1,3              9209 /dev/null
compiz     5948       phil    0r      CHR        1,3              9209 /dev/null
gnome-pan  5951       phil    0r      CHR        1,3              9209 /dev/null
nautilus   5954       phil    0r      CHR        1,3              9209 /dev/null
gnome-vol  5958       phil    0u      CHR        1,3              9209 /dev/null
gnome-vol  5958       phil    1u      CHR        1,3              9209 /dev/null
gnome-vol  5958       phil    2u      CHR        1,3              9209 /dev/null
bonobo-ac  5963       phil    0u      CHR        1,3              9209 /dev/null
bonobo-ac  5963       phil    1u      CHR        1,3              9209 /dev/null
bonobo-ac  5963       phil    2u      CHR        1,3              9209 /dev/null
gnome-vfs  6009       phil    0u      CHR        1,3              9209 /dev/null
gnome-vfs  6009       phil    1u      CHR        1,3              9209 /dev/null
gnome-vfs  6009       phil    2u      CHR        1,3              9209 /dev/null
gnome-vfs  6009       phil    4u      CHR        1,3              9209 /dev/null
gtk-windo  6048       phil    0r      CHR        1,3              9209 /dev/null
compiz.re  6049       phil  mem       CHR      195,0             17193 /dev/nvidia0
compiz.re  6049       phil  mem       CHR        1,5              2870 /dev/zero
compiz.re  6049       phil    0r      CHR        1,3              9209 /dev/null
compiz.re  6049       phil    5u      CHR    195,255             17187 /dev/nvidiactl
compiz.re  6049       phil    6u      CHR      195,0             17193 /dev/nvidia0
compiz.re  6049       phil    7u      CHR      195,0             17193 /dev/nvidia0
compiz.re  6049       phil    8u      CHR      195,0             17193 /dev/nvidia0
compiz.re  6049       phil    9u      CHR      195,0             17193 /dev/nvidia0
vino-sess  6051       phil    0r      CHR        1,3              9209 /dev/null
update-no  6059       phil    0r      CHR        1,3              9209 /dev/null
trackerd   6065       phil    0r      CHR        1,3              9209 /dev/null
gnome-scr  6069       phil    0r      CHR        1,3              9209 /dev/null
gnome-scr  6069       phil    1u      CHR        1,3              9209 /dev/null
gnome-scr  6069       phil    2u      CHR        1,3              9209 /dev/null
mapping-d  6071       phil    0r      CHR        1,3              9209 /dev/null
gnome-pow  6091       phil    0u      CHR        1,3              9209 /dev/null
gnome-pow  6091       phil    1u      CHR        1,3              9209 /dev/null
gnome-pow  6091       phil    2u      CHR        1,3              9209 /dev/null
trashappl  6129       phil    0u      CHR        1,3              9209 /dev/null
trashappl  6129       phil    1u      CHR        1,3              9209 /dev/null
trashappl  6129       phil    2u      CHR        1,3              9209 /dev/null
gweather-  6179       phil    0u      CHR        1,3              9209 /dev/null
gweather-  6179       phil    1u      CHR        1,3              9209 /dev/null
gweather-  6179       phil    2u      CHR        1,3              9209 /dev/null
pidgin     6184       phil    0r      CHR        1,3              9209 /dev/null
notificat  6364       phil    0u      CHR        1,3              9209 /dev/null
notificat  6364       phil    1u      CHR        1,3              9209 /dev/null
notificat  6364       phil    2u      CHR        1,3              9209 /dev/null
notificat  6364       phil    4u      CHR        1,3              9209 /dev/null
kdeinit    6755       phil    0r      CHR        1,3              9209 /dev/null
dcopserve  6758       phil    0r      CHR        1,3              9209 /dev/null
klauncher  6761       phil    0r      CHR        1,3              9209 /dev/null
kget      11301       phil    0r      CHR        1,3              9209 /dev/null
kget      11301       phil   67r      CHR      116,2             14939 /dev/snd/timer
kget      11301       phil   68u      CHR      116,5             15220 /dev/snd/pcmC0D0p
kget      11301       phil   69u      CHR      116,7             15248 /dev/snd/controlC0
knotify   11328       phil    0r      CHR        1,3              9209 /dev/null
kio_uiser 11433       phil    0r      CHR        1,3              9209 /dev/null
kio_file  29847       phil    0r      CHR        1,3              9209 /dev/null



---

### Post by dethredic on 2008-02-13
anyone?

---

### Post by MighMoS on 2008-02-13
It looks like for some reason kget may be hogging your sound (from looking at at the lines```
kget 11301 phil 67r CHR 116,2 14939 /dev/snd/timer
kget 11301 phil 68u CHR 116,5 15220 /dev/snd/pcmC0D0p
kget 11301 phil 69u CHR 116,7 15248 /dev/snd/controlC0
```. Does your sound always go out when running kget (or other KDE apps?)

---

### Post by dethredic on 2008-02-13
I know my sound has gone out when I have not had not run kget yet. I don't know of any other kde apps that I use.

---

### Post by Jeanpaul145 on 2008-02-13
I just had the same problem were Amarok would give me the same Xine message.
I just restarted Amarok and sound is working fine now. Methinks it's the typical case of aRts and ESD clashing.

Pulseaudio anyone ;) ?

---

### Post by dethredic on 2008-02-14
> **Jeanpaul145 said:**
> I just had the same problem were Amarok would give me the same Xine message.
I just restarted Amarok and sound is working fine now. Methinks it's the typical case of aRts and ESD clashing.

Pulseaudio anyone ;) ?

Can you explain further? I do not understand.

---

### Post by Jeanpaul145 on 2008-02-14
> **dethredic said:**
> Can you explain further? I do not understand.

Well, I use Amarok in gnome (some say that's a dumb thing to do, but what can I say? I like the gnome interface, but I like most KDE apps better than the "gnome equivalents" :p ).
So sometimes Amarok will be running (which requires aRts functionality), but for instance I also use Totem Media Player (because it integrates nicely in gnome), which requires ESD AFAIK. In some circumstances, Amarok OR Totem (or both?) will fail to tell the sound card that they're not using it anymore, so that will stay blocked. When The other tries to acquire a lock, that will fail and hence, no sound.
If I'm not mistaken PulseAudio tries to clean up meses like these by keeping a constant lock on the sound card itself and "emulating" ESD for apps that use it. I don't know about aRts, since KDE4 is doing its own thing, but I'd be surprised if it didn't :)

---

### Post by dethredic on 2008-02-14
ok, I will try it out

---

### Post by dethredic on 2008-02-15
Ok, I installed Pulseaudio, and then waited for my sound to stop working. Well sure enough it did, so I opened up Pulseaudio and I was unsure how to use it.

In the tray icon there were default server, default sink and default source. The all were the same and had:
> No Network devices Found   <- that was greyed out
o Default     <- o = circle check thing
o Other

So, what am I suposed to do with it?

---

### Post by Jeanpaul145 on 2008-02-16
> **dethredic said:**
> Ok, I installed Pulseaudio, and then waited for my sound to stop working. Well sure enough it did, so I opened up Pulseaudio and I was unsure how to use it.

In the tray icon there were default server, default sink and default source. The all were the same and had:


So, what am I suposed to do with it?

Yeah, when I said "PulseAudio anyone?" I was referring to Hardy, where it is installed (and configured, as far as that is needed) by default.
I suppose there are ways to make it work in Gutsy, However I don't have any personal experience with that.

---

### Post by dethredic on 2008-02-16
Ok, Darn. 

Back to square 1.

---

### Post by Jeanpaul145 on 2008-02-16
> **dethredic said:**
> Ok, Darn. 

Back to square 1.

Not necessarily. Let me search for a tutorial, maybe that can help you out.

---

### Post by Jeanpaul145 on 2008-02-17
[Here]("https://wiki.ubuntu.com/PulseAudio") is a tutorial that **should be able to** help you out:popcorn:

[This]("http://www.linux.com/feature/119926") will surely be helpful as well.

---

### Post by giosico on 2008-05-28
lsof | grep pcm
kill the process listing /dev/snd/pcmC0D0p
audio apps should start working again
for me firefox 3 beta 5 is the culprit

when my audio drops out on ubuntu hardy
movie player cant even play the video properly
vlc has no audio

---

