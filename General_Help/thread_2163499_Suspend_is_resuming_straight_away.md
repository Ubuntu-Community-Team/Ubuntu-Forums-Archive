---
title: "Suspend is resuming straight away?"
date: 2013-07-18
forum: General Help
---

### Post by blinkydamo on 2013-07-18
Hi guys,

Been looking around trying to solve this problem and not having much luck.  I have an HP mini 311c which will not go into suspend without me first turning off the wifi/bluetooth by using the hardware buttom on the keyboard.  

I am running Xubuntu 13.04, I have 2.5gb of RAM (512mb being used for the GFX) and a 500mb swap partition that doesn't seem to ever get used.

```
 total       used       free     shared    buffers     cachedMem:          
    2.5G       2.0G       440M         0B       263M       1.0G
-/+ buffers/cache:       806M       1.7G
Swap:         486M         0B       486M



```

This is the contents of the pm-suspend.log, could someone have a look at it and tell me why it is waking instead of staying in suspend.

```
Initial commandline parameters: Thu Jul 18 17:33:34 BST 2013: Running hooks for suspend.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:


/usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
Linux blinky-netbook 3.8.0-25-generic #37-Ubuntu SMP Thu Jun 6 20:47:30 UTC 2013 i686 i686 i686 GNU/Linux
Module                  Size  Used by
coretemp               13131  0 
joydev                 17097  0 
hp_wmi                 17712  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_codec_hdmi     36185  1 
snd_hda_codec_idt      63896  1 
microcode              18286  0 
lib80211_crypt_tkip    17160  0 
wl                   2902185  0 
lib80211               14040  2 wl,lib80211_crypt_tkip
uvcvideo               71279  0 
videobuf2_vmalloc      12920  1 uvcvideo
cfg80211              436177  1 wl
videobuf2_memops       13042  1 videobuf2_vmalloc
videobuf2_core         39161  1 uvcvideo
snd_hda_intel          38307  3 
nvidia               8582455  40 
shpchp                 32129  0 
videodev               95806  2 uvcvideo,videobuf2_core
psmouse                81038  0 
btusb                  17986  0 
serio_raw              13031  0 
snd_hda_codec         117580  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
i2c_nforce2            12876  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
snd                    56485  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12600  1 snd
video                  18894  0 
parport_pc             27504  0 
ppdev                  12817  0 
wmi                    18590  1 hp_wmi
bnep                   17669  2 
rfcomm                 37420  12 
bluetooth             202069  22 bnep,btusb,rfcomm
binfmt_misc            17260  1 
mac_hid                13037  0 
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
forcedeth              61777  0 
ahci                   25507  2 
libahci                26108  1 ahci
             total       used       free     shared    buffers     cached
Mem:       2577304    1973220     604084          0     269720    1028540
-/+ buffers/cache:     674960    1902344
Swap:       498684          0     498684


/usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:


/usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:


/etc/pm/sleep.d/10_grub-common suspend suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:


/usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:


/usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:


/usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
stop: Unknown instance: 


/usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:


/usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:


/usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
nVidia binary video drive detected, not using quirks.


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found
kernel.acpi_video_flags = 0


/usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
Thu Jul 18 17:33:36 BST 2013: performing suspend
Thu Jul 18 17:33:41 BST 2013: Awake.
Thu Jul 18 17:33:41 BST 2013: Running hooks for resume
Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
/usr/lib/pm-utils/sleep.d/99video: 22: /usr/lib/pm-utils/sleep.d/99video: shopt: not found


/usr/lib/pm-utils/sleep.d/99video resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:


/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:


/usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254


/dev/sda:
 setting Advanced Power Management level to 0xfe (254)
 APM_level    = 254


/usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:


/usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:


/usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/90clock resume suspend:


/usr/lib/pm-utils/sleep.d/90clock resume suspend: not applicable.
Running hook /usr/lib/pm-utils/sleep.d/75modules resume suspend:
Reloaded unloaded modules.


/usr/lib/pm-utils/sleep.d/75modules resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend:
Failed to connect to wpa_supplicant - wpa_ctrl_open: No such file or directory


/usr/lib/pm-utils/sleep.d/60_wpa_supplicant resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/50unload_alx resume suspend:


/usr/lib/pm-utils/sleep.d/50unload_alx resume suspend: success.
Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend:


/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: success.
Running hook /etc/pm/sleep.d/10_grub-common resume suspend:


/etc/pm/sleep.d/10_grub-common resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00powersave resume suspend:


/usr/lib/pm-utils/sleep.d/00powersave resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/00logging resume suspend:


/usr/lib/pm-utils/sleep.d/00logging resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000record-status resume suspend:


/usr/lib/pm-utils/sleep.d/000record-status resume suspend: success.
Running hook /usr/lib/pm-utils/sleep.d/000kernel-change resume suspend:


/usr/lib/pm-utils/sleep.d/000kernel-change resume suspend: success.
Thu Jul 18 17:33:42 BST 2013: Finished.



```

I have noticed that the light of the wifi/bluetooth does turn off just before the screen goes dark but then comes back on when the system wakes up again.

Cheers in advance,

Blinky

---

### Post by blinkydamo on 2013-07-19
Anyone got any idea's on this?

Blinky

---

### Post by Toz on 2013-07-19
What happens if you manually unload the wireless module first (from a terminal window):
```
sudo modprobe -r wl
```
...(enter your password when prompted), then:
```
sudo pm-suspend
```
...to suspend.

When the system returns from suspend (resumes), you will need to:
```
sudo modprobe wl
```
...to reload the module to get the wireless working again.

If this process works (the system suspends, stays suspended and on resume the wireless works again), then we can automate the process.

---

### Post by blinkydamo on 2013-07-19
Cheers for the reply, unfortunatly it didn't work, system went for the suspend then woke up again.

Any other idea's?

Cheers,

Blinky.

---

### Post by Toz on 2013-07-19
Lets try the same but now also add the bluetooth stuff:
```
sudo modprobe -r wl bnep btusb rfcomm bluetooth
```
...then suspend and see.

To restore the modules:
```
sudo modprobe bluetooth
sudo modprobe rfcomm
sudo modprobe btusb
sudo modprobe bnep
sudo modprobe wl
```

---

### Post by blinkydamo on 2013-08-06
Toz - 

Sorry for the late reply, what with the forum problems and a few things at home I have not had chance to drop in and have a look at your response.  I have tried what you suggested and still the same.

If I manually turn off the wifi/bluetooth it'll work but everything else rewakes that system.  It goes back to a black screen and when I move the mouse I get a prompt for my password.

Cheers again for your help so far.

Blinky

---

### Post by Toz on 2013-08-06
How about if you:
```
sudo rfkill block wifi
sudo rfkill block bluetooth
```
...then try suspending? On resume, you will need to:
```
sudo rfkill unblock wifi
sudo rfkill unblock bluetooth
```
...to get them back.

---

### Post by blinkydamo on 2013-08-06
That worked a treat mate, so the next question is how to get that to work in one click.  Also I would like to be able to keep the bluetooth turned off as I never use it.  Is this possible without causing a problem with the suspend?

Cheers,

Blinky

---

### Post by Toz on 2013-08-06
Better yet, lets automate it. But first, can you try to see if its only bluetooth that is blocking the suspend? To do so, run:
```
sudo rfkill bluetooth
```
...and try suspending. 

If it works, do only #1 below.
If it doesn't work, do both #1 and #2 below.

1. To disable bluetooth:
```
gksu mousepad /etc/rc.local
```
...and above the *exit 0* command, add:
```
rfkill block bluetooth
```
...save the file.

2. To automate the block/unblock of the wifi:
```
gksu mousepad /etc/pm/sleep.d/wifi
```
...and copy/paste this code:
```
#!/bin/bash
case "$1" in
	suspend)
		rfkill block wifi
		;;
	resume) 
		rfkill unblock wifi
		;;
	*) exit $NA
		;;
esac

```
...and make the file executable:
```
sudo chmod +x /etc/pm/sleep.d/wifi
```
...it will take effect on the next sleep attempt.

---

### Post by blinkydamo on 2013-08-06
Toz you are amazing mate, the script works brilliantly.  I have not been able to disable the bluetooth though using rfkill as it also kills the wifi.

This is the rfkill list:

3: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
6: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
7: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Any ideas how to kill the bluetooth only?

Cheers for all the help.

Blinky.

---

### Post by Toz on 2013-08-06
Try this to disable bluetooth. Edit /etc/bluetooth/main.conf and change "InitiallyPowered" to "false". Save and reboot to test if it works.

---

### Post by blinkydamo on 2013-08-06
Just tried that before you posted and still on.  I am reading about blacklisting, is it that correct course to take or will be make more problems for me?

Blinky

---

### Post by Toz on 2013-08-06
Is there a setting in your bios maybe that turns it off?

---

### Post by Toz on 2013-08-06
Here is a link with 5 different ways: [http://linuxg.net/how-to-disable-bluetooth-at-startup-5-practical-methods/]("http://linuxg.net/how-to-disable-bluetooth-at-startup-5-practical-methods/")

---

### Post by blinkydamo on 2013-08-06
No mate, I will keep looking into this one for a bit more.  Thank you very much for you help sorting the sleep issue, will come in handy when I start Uni in September.

I do have one more question for you if you are up for it :)

When my screen turns off after inactivity the backlight is staying on, any ideas where to start?

Cheers again,

Blinky

---

### Post by Toz on 2013-08-06
If you can't separate bluetooth from wireless, then just use this as your /etc/pm/sleep.d/wifi script:
```

#!/bin/bash
case "$1" in
	suspend)
                rfkill block bluetooth
		rfkill block wifi
		;;
	resume) 
		rfkill unblock wifi
                rfkill unblock bluetooth
		;;
	*) exit $NA
		;;
esac
```

---

### Post by blinkydamo on 2013-08-06
The script works just blocking the wifi.  The light on the keyboard goes out as it shuts down and the comes back when it wakes.  So with that I am amazingly happy.

Cheers again,

Blinky

---

