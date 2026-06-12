---
title: "Can't adjust brightness on my laptop running Ubuntu 12.10"
date: 2013-06-20
forum: General Help
---

### Post by SubjectSigma on 2013-06-20
Hello, recently I installed ubuntu 12.10 on my laptop (Sony Vaio E series vpceg1bfx) and everything seems to work fine except that I can't change the brightness without the use of terminal commands and even then I have to do it every time i boot, which is often. The Fn + F5/F6 seem to work but the slider only moves one setting away from  the max and doesn't affect the actual screen brightness anyway. I'm still very new to this so maybe I'm missing something. Thanks in advance.

---

### Post by Toz on 2013-06-20
Hello and welcome to the forums.

Is this the model that has only the intel graphics? 

And have you tried any kernel parameters? If not, I would suggest the following:
```
acpi_backlight=vendor
```
...have a look at the "Kernel Boot Parameters" link in my signature for information on how to test kernel parameters.

If that parameter doesn't work, you might want to try these:
```
acpi_osi=Linux
```
```
acpi_osi=Linux acpi_backlight=vendor
```
```
acpi_osi=
```

---

### Post by SubjectSigma on 2013-06-21
Yes it is the model with Intel 3000 graphics. I tried all of those kernel parameters and all of them (aside from the first one) fixed the brightness meter however while the value on the meter changes the actual brightness still does not.

---

### Post by Toz on 2013-06-21
Can you try the **acpi_osi=Linux acpi_backlight=vendor** kernel parameters again, and this time post back the results of the following commands while these parameters are in use:

1. Show the current kernel boot line:
```
cat /proc/cmdline
```

2. Show the backlight interfaces and values:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

3. Show loaded modules:
```
lsmod
```

4. Your dmesg log file:
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

---

### Post by SubjectSigma on 2013-06-21
These are the results after entering those commands:


1) BOOT_IMAGE=/boot/vmlinuz-3.5.0-34-generic root=UUID=bb104b0d-815b-4001-bfae-970b0c2086da ro reboot=acpi quiet splash acpi_osi=Linux acpi_backlight=vendor vt.handoff=7

2) /sys/class/backlight/intel_backlight
4882
4882
/sys/class/backlight/sony
6
7


3) Module                  Size  Used by
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_conexant    61898  1 
parport_pc             32689  0 
rfcomm                 46620  0 
ppdev                  17074  0 
bnep                   18141  2 
bluetooth             209249  10 rfcomm,bnep
coretemp               13401  0 
kvm                   414111  0 
ghash_clmulni_intel    13221  0 
cryptd                 20404  1 ghash_clmulni_intel
joydev                 17458  0 
acer_wmi               32454  0 
sparse_keymap          13891  1 acer_wmi
microcode              22804  0 
snd_hda_intel          33492  3 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
psmouse               100389  0 
serio_raw              13216  0 
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
arc4                   12530  2 
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
videodev              120310  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
sony_laptop            54040  0 
wmi                    19071  1 acer_wmi
ath9k                 131317  0 
mei                    40691  0 
i915                  520799  3 
mac80211              535936  1 ath9k
drm_kms_helper         49113  1 i915
ath9k_common           14056  1 ath9k
ath9k_hw              395357  2 ath9k,ath9k_common
ath                    23828  3 ath9k,ath9k_common,ath9k_hw
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rtsx_pci_ms            13012  0 
mac_hid                13206  0 
memstick               16555  1 rtsx_pci_ms
cfg80211              206797  3 ath9k,mac80211,ath
lpc_ich                17062  0 
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
drm                   288436  4 i915,drm_kms_helper
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
i2c_algo_bit           13414  1 i915
video                  19391  2 acer_wmi,i915
hid_logitech_dj        18605  0 
usbhid                 46987  1 hid_logitech_dj
hid                   100411  2 hid_logitech_dj,usbhid
rtsx_pci_sdmmc         17476  0 
ahci                   25721  2 
libahci                31192  1 ahci
atl1c                  41102  0 
rtsx_pci               33452  2 rtsx_pci_ms,rtsx_pci_sdmmc


4) The program 'pastebinit' can be found in the following packages:
 * pastebinit
 * pastebinit
Try: sudo apt-get install <selected package>

---

### Post by SubjectSigma on 2013-06-21
Here's a screenshot of the module list:

[http://imgur.com/lHxzpgj](http://imgur.com/lHxzpgj)
[http://imgur.com/HBeapQh](http://imgur.com/HBeapQh)

---

### Post by Toz on 2013-06-21
You have 2 backlight interfaces: intel_backlight and sony. This is the problem. 

First, lets see which one is the active one. Run the following commands and tell me which ones make a change to the brightness:
```

echo 2441 | sudo tee /sys/class/backlight/intel_backlight/brightness
echo 3882 | sudo tee /sys/class/backlight/intel_backlight/brightness
echo 4882 | sudo tee /sys/class/backlight/intel_backlight/brightness

```

```

echo 3 | sudo tee /sys/class/backlight/sony/brightness
echo 5 | sudo tee /sys/class/backlight/sony/brightness
echo 7 | sudo tee /sys/class/backlight/sony/brightness

```

If you have a look at [this thread]("http://ubuntuforums.org/showthread.php?t=2033273"), I helped someone else with a Sony E series and we had to create a workaround to get the brightness to work. I think we may have to do the same for your computer.

We might as well get the key codes for your brightness keys now. Open a terminal window and type in the following command:
```
acpi_listen
```
...then press the brightness up key combination followed by thee brightness down key combination. Post back the codes that are displayed in the terminal window.

---

### Post by SubjectSigma on 2013-06-22
The first set of codes changed the brightness, but not the second.

Here's the list that came up from the acpi_listen:

frankie@SubjectSigma:~$ acpi_listen
sony/hotkey SNC 00000001 00000011
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000011
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000011
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000010
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000010
sony/hotkey SNC 00000001 0000003b
sony/hotkey SNC 00000001 00000010
sony/hotkey SNC 00000001 0000003b

---

### Post by Toz on 2013-06-22
Okay. If you want to fix this problem properly, it is best to [file a bug report with launchpad]("https://help.ubuntu.com/community/ReportingBugs") against the **linux** package.

Here is a workaround that should get the function keys and brightness working on your laptop again:
 
[LIST=1]
[*]Create the brightness up hook:
```
gksu gedit /etc/acpi/events/sony-brightness-up
```
...and copy/paste this code:
```
event=sony/hotkey SNC 00000001 00000011
action=/etc/acpi/brightup.sh
```
...and save the file.
.
[*]Create the brightness down hook:
```
gksu gedit /etc/acpi/events/sony-brightness-down
```
...and copy/paste this code:
```
event=sony/hotkey SNC 00000001 00000010
action=/etc/acpi/brightdown.sh
```
...and save the file.
.
[*]Create the script to increase brightness:
```
gksu gedit /etc/acpi/brightup.sh
```
...and copy/paste this code:
```
#!/bin/bash

curr=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ $curr -lt 4272 ]; then
curr=$((curr+610));
echo $curr  > /sys/class/backlight/intel_backlight/brightness;
fi
```
...and save the file.
[*]Create the script to decrease brightness:
```
gksu gedit /etc/acpi/brightdown.sh
```
...and copy/paste the following code:
```
#!/bin/bash

curr=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ $curr -gt 610 ]; then
curr=$((curr-610));
echo $curr  > /sys/class/backlight/intel_backlight/brightness;
fi
```
...and save the file.
[*]Make the scripts executable:
```
sudo chmod +x /etc/acpi/events/sony-brightness-up
sudo chmod +x /etc/acpi/events/sony-brightness-down
sudo chmod +x /etc/acpi/brightup.sh
sudo chmod +x /etc/acpi/brightdown.sh
```
[*]Restart the acpid daemon:
```
sudo service acpid restart
```
[*]Give it a go.
[*]
[/LIST]

---

### Post by SubjectSigma on 2013-06-23
Everything worked up until step 5, then it said "no such file or directory."




Edit: Just tried it again and it seemed to work but the brightness still does not change.

---

### Post by Toz on 2013-06-23
Can you post back the contents of each of the files as well as the results of:
```
ls -l /etc/acpi/events
ls -l /etc/acpi
```

---

### Post by SubjectSigma on 2013-06-24
frankie@SubjectSigma:~$ ls -l /etc/acpi/events
total 140
-rw-r--r-- 1 root root 116 Oct  9  2012 ac
-rw-r--r-- 1 root root 239 Oct  9  2012 asus-f8sv-touchpad
-rw-r--r-- 1 root root 271 Oct  9  2012 asus-keyboard-backlight-down
-rw-r--r-- 1 root root 265 Oct  9  2012 asus-keyboard-backlight-up
-rw-r--r-- 1 root root 217 Oct  9  2012 asus-media-eject
-rw-r--r-- 1 root root 215 Oct  9  2012 asus-rotate
-rw-r--r-- 1 root root 238 Oct  9  2012 asus-touchpad
-rw-r--r-- 1 root root 155 Oct  9  2012 asus-video
-rw-r--r-- 1 root root  73 Oct  9  2012 asus-wireless-off
-rw-r--r-- 1 root root  72 Oct  9  2012 asus-wireless-on
-rw-r--r-- 1 root root 126 Oct  9  2012 battery
-rw-r--r-- 1 root root 223 Oct  9  2012 ibm-wireless
-rw-r--r-- 1 root root 279 Oct  9  2012 lenovo-touchpad
-rw-r--r-- 1 root root 218 Oct  9  2012 lenovo-touchpad2
-rw-r--r-- 1 root root  67 Oct  9  2012 lenovo-undock
-rw-r--r-- 1 root root 118 Oct  9  2012 lidbtn
-rw-r--r-- 1 root root 218 Oct  9  2012 panasonic-lockbtn
-rw-r--r-- 1 root root 423 Jun  7  2012 powerbtn
-rw-r--r-- 1 root root 315 Oct  9  2012 sleepbtn
-rwxr-xr-x 1 root root  71 Jun 23 11:29 sony-brightness-down
-rwxr-xr-x 1 root root  69 Jun 23 11:27 sony-brightness-up
-rw-r--r-- 1 root root 277 Oct  9  2012 thinkpad-cmos
-rw-r--r-- 1 root root  68 Oct  9  2012 tosh-battery
-rw-r--r-- 1 root root  70 Oct  9  2012 tosh-hibernate
-rw-r--r-- 1 root root  66 Oct  9  2012 tosh-ibutton
-rw-r--r-- 1 root root  66 Oct  9  2012 tosh-lock
-rw-r--r-- 1 root root  65 Oct  9  2012 tosh-mail
-rw-r--r-- 1 root root  66 Oct  9  2012 tosh-media
-rw-r--r-- 1 root root  65 Oct  9  2012 tosh-next
-rw-r--r-- 1 root root  65 Oct  9  2012 tosh-play
-rw-r--r-- 1 root root  65 Oct  9  2012 tosh-prev
-rw-r--r-- 1 root root  65 Oct  9  2012 tosh-stop
-rw-r--r-- 1 root root 222 Oct  9  2012 tosh-wireless
-rw-r--r-- 1 root root  64 Oct  9  2012 tosh-www
-rw-r--r-- 1 root root   0 Jun 23 11:28 Untitled Document 1
-rw-r--r-- 1 root root   0 Jun 23 11:29 Untitled Document 2
-rw-r--r-- 1 root root  80 Oct  9  2012 videobtn
frankie@SubjectSigma:~$ ls -l /etc/acpi
total 112
-rwxr-xr-x 1 root root  391 Oct  9  2012 asus-keyboard-backlight.sh
-rwxr-xr-x 1 root root  806 Oct  9  2012 asus-touchpad.sh
-rwxr-xr-x 1 root root  180 Oct  9  2012 asus-wireless.sh
-rwxr-xr-x 1 root root  135 Oct  9  2012 batterybtn.sh
-rwxr-xr-x 1 root root  192 Jun 23 11:30 brightup.sh
-rwxr-xr-x 1 root root  134 Oct  9  2012 ejectbtn.sh
drwxr-xr-x 2 root root 4096 Jun 23 11:29 events
-rwxr-xr-x 1 root root  215 Oct  9  2012 hibernate.sh
-rwxr-xr-x 1 root root  608 Oct  9  2012 ibm-wireless.sh
-rwxr-xr-x 1 root root 1282 Oct  9  2012 lid.sh
-rwxr-xr-x 1 root root  134 Oct  9  2012 lockbtn.sh
-rwxr-xr-x 1 root root  270 Oct  9  2012 mailbtn.sh
-rwxr-xr-x 1 root root  132 Oct  9  2012 mediabtn.sh
-rwxr-xr-x 1 root root  135 Oct  9  2012 nextbtn.sh
-rwxr-xr-x 1 root root  136 Oct  9  2012 playbtn.sh
-rwxr-xr-x 1 root root 2144 Jun  7  2012 powerbtn.sh
-rwxr-xr-x 1 root root  209 Oct  9  2012 power.sh
-rwxr-xr-x 1 root root  139 Oct  9  2012 prevbtn.sh
-rwxr-xr-x 1 root root  720 Oct  9  2012 rotatescreen.sh
-rwxr-xr-x 1 root root  359 Oct  9  2012 screenblank.sh
-rwxr-xr-x 1 root root  398 Oct  9  2012 sleepbtn.sh
-rwxr-xr-x 1 root root 1280 Oct  9  2012 sleep.sh
-rwxr-xr-x 1 root root  133 Oct  9  2012 stopbtn.sh
-rwxr-xr-x 1 root root  948 Oct  9  2012 thinkpad-stretchortouchpad.sh
-rwxr-xr-x 1 root root  455 Oct  9  2012 tosh-wireless.sh
-rwxr-xr-x 1 root root  238 Oct  9  2012 undock.sh
-rwxr-xr-x 1 root root  135 Oct  9  2012 videobtn.sh
-rwxr-xr-x 1 root root  130 Oct  9  2012 webbtn.sh
frankie@SubjectSigma:~$

---

### Post by Toz on 2013-06-24
You are missing the /etc/acpi/brightdown.sh file. Please add.

If you run the files manually from the command line:
```
sudo /etc/acpi/brightdown.sh
```
...and
```
sudo /etc/acpi/brightup.sh
```

Does the brightness change? Do you get any error messages?

Also remember to:
```
sudo service acpid restart
```
...then retry the brightness function keys.

---

### Post by NikTh on 2013-06-24
Man !!! , you are something else.. 
:guitar:

I tested the workaround (scripts) in my laptop (Acer - Intel only) and it worked as it should. No kernel parameters anymore :)

---

### Post by SubjectSigma on 2013-06-27
I entered the codes and everything seems to be working now! Thanks a lot for taking your time to help me with this!

---

### Post by ZPC2THLgate on 2013-07-01
I gotta run some errands atm but I'll give those a try and let you guys know how it went. Thanks a lot.































__________________________________________________________
[ZOPO Phone](http://www.zopo-mobile-shop.com/zopo-mobile-phone.html) [ZOPO ZP910](http://www.zopo-mobile-shop.com/zopo-zp910-andriod-4-1-mtk6589-quad-core-smart-phone-5-3-inch-ips-qhd-screen-1g-ram-5-0mp-front-camera-white.html) [ZOPO C2](http://www.zopo-mobile-shop.com/zopo-c2-aliyun-os-quad-core-1-5ghz-smart-phone-5-0-inch-1080p-fhd-screen-5-0mp-front-camera-1g-16g.html)

---

### Post by NikTh on 2013-08-01
What's wrong now ? I cannot understand. I upgraded to 12.04.2 (daily iso), so now I have 3.8 kernel and X-stack of raring. I think this is no matter, but I felt I had to tell. 

I tried the scripts but no go. 

Here are all.. 

**cat /etc/acpi/acer-brn-up.sh**
```
#!/bin/bash

curr=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ $curr -lt 896 ]; then
curr=$((curr+80));
echo $curr  > /sys/class/backlight/intel_backlight/brightness;
fi
```
**cat /etc/acpi/acer-brn-down.sh**
```
#!/bin/bash

curr=`cat /sys/class/backlight/intel_backlight/actual_brightness`
if [ $curr -gt 80 ]; then
curr=$((curr-80));
echo $curr  > /sys/class/backlight/intel_backlight/brightness;
fi
```
**cat /etc/acpi/events/acer-brightness-up**
```
event=video DD03 00000086 00000000
action=/etc/acpi/acer-brn-up.sh
```
**cat /etc/acpi/events/acer-brightness-down**
```
event=video DD03 00000087 00000000
action=/etc/apci/acer-brn-down.sh
``` 
The events are correct. Checked with ```
acpi_listen
``` 
**for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done**
```
/sys/class/backlight/acpi_video0
9
9
/sys/class/backlight/intel_backlight
976
976
``` 

```
echo 800 | sudo tee /sys/class/backlight/intel_backlight/brightness
``` 
Works. 

**for i in /etc/acpi/acer-*; do stat -c "%a %n" $i; done  && for i in /etc/acpi/events/acer-brightness-*; do stat -c "%a %n" $i; done **
```
755 /etc/acpi/acer-brn-down.sh
755 /etc/acpi/acer-brn.up.sh
755 /etc/acpi/events/acer-brightness-down
755 /etc/acpi/events/acer-brightness-up
``` 



:confused:

**UPDATE: **

I ran the scripts from terminal.. and I got a weird output on acer-brn-down.sh 

```
./acer-brn-down.sh 
./acer-brn-down.sh: line 6: /sys/class/backlight/intel_backlight/brightness: Permission denied
```

Why is that ? 

The contests of the scripts are above and the acer-brn-up.sh works, without permission problem !

---

### Post by Toz on 2013-08-01
Hmmm. Is acpid running? Can you try restarting it?
```
sudo service acpid restart
```
And also look at syslog for acpid messages:
```
cat /var/log/syslog | grep acpid
```

---

### Post by Toz on 2013-08-01
> **NikTh said:**
> **UPDATE: **

I ran the scripts from terminal.. and I got a weird output on acer-brn-down.sh 

```
./acer-brn-down.sh 
./acer-brn-down.sh: line 6: /sys/class/backlight/intel_backlight/brightness: Permission denied
```

Why is that ? 

The contests of the scripts are above and the acer-brn-up.sh works, without permission problem !
The scripts need to run as root (use sudo). When run through acpid, they are run as root.

---

### Post by NikTh on 2013-08-01
Never mind Toz, sorry to bothered  you  :( 

It was a typo.. (damn! my eyes) 

Look the **acer-brightness-down **event. I corrected here in forum, but didn't see it in terminal.. :P 

It works OK ! 

Thanks

---

