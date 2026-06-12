---
title: "brightness changing by itself on 15.10"
date: 2016-02-18
forum: General Help
---

### Post by victinigjw on 2016-02-18
ubuntu 15.10 on msi notebook(i7 + gtx970m).
I already using nvidia x server and intel driver, but the brightness always change automatically.
sometime it goes up to 75%, sometimes it just turn black(screen is off, can light up again with fn + up).
this "auto jumping" is really annoying, please help me figure out what's wrong, thanks!

---

### Post by Scott Deagan on 2016-02-20
[FONT=arial]If you are using the Intel GPU, you could always try to set your backlighting level in your rc.local:

[/FONT]1. Open a terminal.[FONT=arial][/FONT]
[FONT=arial]2.[/FONT] [FONT=courier new]sudo vi /etc/rc.local[/FONT]
[FONT=arial]3. Add (before the line containing[/FONT] [FONT=courier new]exit 0[/FONT]): [FONT=courier new]echo 10 > /sys/class/[/FONT][FONT=courier new]backlight/intel_backlight/brightness[/FONT]
[FONT=arial]4. Save the file and reboot to see if it works.
[SIZE=2]
[/SIZE][/FONT][SIZE=2][SIZE=4][FONT=arial]To insert text  using the vi editor, position the cursor to where you would like to  start typing and then press the 'i' key.To save the file and exit the vi  editor, press the ESC key, then the ":" key, then type "wq" and press  enter.[/FONT][/SIZE]

[/SIZE][FONT=arial][/FONT]Of course, you can change the value of 10 to whatever brightness you prefer.[FONT=arial]
[SIZE=1]
[/SIZE][/FONT]

---

### Post by andrey14 on 2016-03-09
Ubuntu 15.10, msi gs60 (i7-5700HQ, graphics intel + nvidia), last updates.
Same problem, very annoying. 
Sometimes brightness keep staing as needed, sometimes it changes itself randomly up to once a minute.
Changes itself any random level 0 to 100%.

Affected:
 - Both power modes: battery and plugged in. 
 - GPU: Intel  - affected. Nvidia - don't use usually, so don't know.


[**[COLOR=#000000]Scott Deagan[/COLOR]**]("http://ubuntuforums.org/member.php?u=879362"), your comment - it's just a method to change brightness by commandline, it doesn't stops the problem.

---

### Post by jeremy31 on 2016-03-09
Post ```
xinput list
```

---

### Post by andrey14 on 2016-03-10
[**[COLOR=#000000]jeremy31[/COLOR]**]("http://ubuntuforums.org/member.php?u=1924242"),
```
$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Compx 2.4G Receiver                         id=12    [slave  pointer  (2)]
&#9116;   &#8627; Compx 2.4G Receiver                         id=13    [slave  pointer  (2)]
&#9116;   &#8627; ETPS/2 Elantech Touchpad                    id=16    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=8    [slave  keyboard (3)]
    &#8627; Power Button                                id=9    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=10    [slave  keyboard (3)]
    &#8627; Compx 2.4G Receiver                         id=11    [slave  keyboard (3)]
    &#8627; BisonCam, NB Pro                            id=14    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=15    [slave  keyboard (3)]
    &#8627; MSI WMI hotkeys                             id=17    [slave  keyboard (3)]
```
any ideas?

Also tried to catch the process, that changes. No success 
```
sudo auditctl -w /sys/class/backlight/intel_backlight/brightness -p wa
```

---

### Post by jeremy31 on 2016-03-10
Is there also an acpi video entry in /sys/class/backlight/ that might be worth monitoring.  You may also want to check the /var/log/Xorg.0.log

I was thinking it might be caused by an ambient light sensor

---

### Post by andrey14 on 2016-03-10
There is only 1 entry:
$ ls -l /sys/class/backlight/
lrwxrwxrwx 1 root root 0 Mar 10 15:50 intel_backlight -> ../../devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight

Same in /var/log/Xorg.0.log:
[    22.388] (--) intel(0): Found backlight control interface intel_backlight (type 'raw') for output eDP1

Btw, there is something that looks like an ambient light sensor close to the  laptop camera.

---

### Post by jeremy31 on 2016-03-10
Try ```
echo "options msi-laptop auto_brightness=0" | sudo tee /etc/modprobe.d/msi-laptop.conf
```

Reboot

If it doesn't work post ```
ls /sys/devices/platform/msi-laptop-pf/
```
And
```
ls /sys/class/backlight/msi-laptop-bl/
```

And parameter settings might be found with ```
for p in /sys/module/msi-laptop/parameters/*; do echo $p; cat $p; done
```

---

### Post by qrees on 2016-03-26
I have the same issue.

/sys/devices/platform/msi-laptop-pf/ is not available

after running:
```
modprobe msi-laptop
```

The directory is available:
```
auto_fan  bluetooth  driver  driver_override  eco_mode  modalias  power  rfkill  subsystem  touchpad  turbo_cooldown  turbo_mode  uevent  wlan
```

Before and after modprobe brightness changes by itself randomly.

```
root@xubuntu:/sys/module/msi_laptop# ls /sys/class/backlight/msi-laptop-bl/
ls: cannot access /sys/class/backlight/msi-laptop-bl/: No such file or directory

```

```
root@xubuntu:/sys/module/msi_laptop# for p in /sys/module/msi_laptop/parameters/*; do echo $p; cat $p; done
/sys/module/msi_laptop/parameters/*
cat: /sys/module/msi_laptop/parameters/*: No such file or directory
```

It looks like this issue is not affected by msi-laptop module, although I did not add "auto_brightness=0" option.

Any ideas?

---

### Post by jeremy31 on 2016-03-27
> **qrees said:**
> I have the same issue.

/sys/devices/platform/msi-laptop-pf/ is not available

after running:
```
modprobe msi-laptop
```

The directory is available:
```
auto_fan  bluetooth  driver  driver_override  eco_mode  modalias  power  rfkill  subsystem  touchpad  turbo_cooldown  turbo_mode  uevent  wlan
```

Before and after modprobe brightness changes by itself randomly.

```
root@xubuntu:/sys/module/msi_laptop# ls /sys/class/backlight/msi-laptop-bl/
ls: cannot access /sys/class/backlight/msi-laptop-bl/: No such file or directory

```

```
root@xubuntu:/sys/module/msi_laptop# for p in /sys/module/msi_laptop/parameters/*; do echo $p; cat $p; done
/sys/module/msi_laptop/parameters/*
cat: /sys/module/msi_laptop/parameters/*: No such file or directory
```

It looks like this issue is not affected by msi-laptop module, although I did not add "auto_brightness=0" option.

Any ideas?
What modules are loaded ```
lsmod
```

---

### Post by qrees on 2016-03-28
```
Module                  Size  Used by
rfcomm                 69632  12
drbg                   32768  1
ansi_cprng             16384  0
ctr                    16384  1
ccm                    20480  1
bnep                   20480  2
snd_hda_codec_hdmi     49152  1
snd_hda_codec_realtek    86016  1
snd_hda_codec_generic    77824  1 snd_hda_codec_realtek
arc4                   16384  2
msi_wmi                16384  0
sparse_keymap          16384  1 msi_wmi
snd_hda_intel          36864  3
snd_hda_codec         135168  4 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel
snd_hda_core           65536  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
snd_hwdep              16384  1 snd_hda_codec
intel_rapl             20480  0
iosf_mbi               16384  1 intel_rapl
x86_pkg_temp_thermal    16384  0
intel_powerclamp       16384  0
coretemp               16384  0
kvm_intel             167936  0
snd_pcm               102400  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
kvm                   512000  1 kvm_intel
crct10dif_pclmul       16384  0
crc32_pclmul           16384  0
ghash_clmulni_intel    16384  0
iwlmvm                294912  0
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
mac80211              733184  1 iwlmvm
aesni_intel           167936  2
aes_x86_64             20480  1 aesni_intel
lrw                    16384  1 aesni_intel
gf128mul               16384  1 lrw
glue_helper            16384  1 aesni_intel
ablk_helper            16384  1 aesni_intel
cryptd                 20480  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
iwlwifi               200704  1 iwlmvm
input_leds             16384  0
snd_timer              32768  2 snd_pcm,snd_seq
serio_raw              16384  0
snd                    81920  17 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
cfg80211              548864  3 iwlwifi,mac80211,iwlmvm
soundcore              16384  1 snd
joydev                 20480  0
btusb                  45056  0
mei_me                 32768  0
btrtl                  16384  1 btusb
btbcm                  16384  1 btusb
mei                    98304  1 mei_me
btintel                16384  1 btusb
bluetooth             516096  37 bnep,btbcm,btrtl,btusb,rfcomm,btintel
shpchp                 36864  0
intel_lpss_acpi        16384  0
intel_lpss             16384  1 intel_lpss_acpi
acpi_als               16384  0
acpi_pad               20480  0
mac_hid                16384  0
kfifo_buf              16384  1 acpi_als
industrialio           61440  2 acpi_als,kfifo_buf
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                49152  3 lp,ppdev,parport_pc
autofs4                40960  2
hid_generic            16384  0
usbhid                 49152  0
nouveau              1388544  0
i915                 1130496  4
mxm_wmi                16384  1 nouveau
ttm                    94208  1 nouveau
i2c_algo_bit           16384  2 i915,nouveau
psmouse               126976  0
drm_kms_helper        126976  2 i915,nouveau
alx                    36864  0
drm                   356352  7 ttm,i915,drm_kms_helper,nouveau
ahci                   36864  2
mdio                   16384  1 alx
libahci                32768  1 ahci
wmi                    20480  3 msi_wmi,mxm_wmi,nouveau
video                  36864  3 i915,msi_wmi,nouveau
pinctrl_sunrisepoint    28672  0
i2c_hid                20480  0
pinctrl_intel          20480  1 pinctrl_sunrisepoint
hid                   118784  4 i2c_hid,hid_generic,usbhid
```

I see only msi_wmi module related to msi and brightness control.

but:
```
echo 50 > /sys/class/backlight/intel_backlight/brightness
```
Does work and changes the brightness. This does not solve the issue, as brightness still changes on its own after a few seconds.

```
rmmod msi_wmi
```
Does not change anything. Brightness control still works and changes on its own.

Non standard kernel options:
```
intel_idle.max_cstate=0
```
system won't boot without this.

---

### Post by jeremy31 on 2016-03-28
Since the echo 50 command works, use it again then ```
sudo chattr +i /sys/class/backlight/intel_backlight/brightness
```

Then maybe dmesg or the kernel log will complain about not being able to change the brightness

---

### Post by qrees on 2016-03-29
:(
```
chattr: Inappropriate ioctl for device while reading flags on /sys/class/backlight/intel_backlight/brightness
```

I tried chmod 000, which did not result in an error, but also did not help. Brightness keeps changing by itself.

Is this managed by i915 module? maybe there is some option for that module?

EDIT:
Other very interesting effect:

```
cat /sys/class/hwmon/hwmon0/temp1_input
```
Also results in random brightness change!

---

### Post by jeremy31 on 2016-03-29
I think i915 provides the backlight interface.  I wonder if the chattr command failed because /sys/class/backlight/intel_backlight is a symbolic link to another location

Is there an auto setting in system settings for brightness & lock or power?

There is actually code in the msi_laptop module for auto brightness adjustment, any setting in BIOS?

---

### Post by qrees on 2016-03-30
> **jeremy31 said:**
> I think i915 provides the backlight interface.  I wonder if the chattr command failed because /sys/class/backlight/intel_backlight is a symbolic link to another location

Is there an auto setting in system settings for brightness & lock or power?

There is actually code in the msi_laptop module for auto brightness adjustment, any setting in BIOS?

nope, chattr does not work at all here.

also no, all auto brightness settings are disabled (I hope so). Forgot to mention - it is xfce, and I've disabled auto brightness setting.

nothing in BIOS.

I've found something like this thanks to fatrace:
```
21:50:51.897905 Xorg(7443): RO /sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/brightness
21:50:51.897905 Xorg(7443): C /sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/brightness
21:51:03.928636 Xorg(7443): O /sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/brightness
21:51:03.928636 Xorg(7443): R /sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/brightness
21:51:03.928636 Xorg(7443): C /sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/brightness
21:51:03.928722 Xorg(7443): W /sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/brightness
21:51:03.928747 Xorg(7443): RCO /sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/brightness
21:51:03.929417 Xorg(7443): RO /sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/brightness
21:51:03.929417 Xorg(7443): C /sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/brightness
21:51:03.929529 Xorg(7443): O /sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/brightness

```

So each time i do "cat" on "temp1_input" file, these lines show up from fatrace.

Also:
If I chmod 444 /sys/devices/pci0000:00/0000:00:02.0/drm/card0/card0-eDP-1/intel_backlight/brightness before starting Xorg server, brightness stops changing at all. This only works if the permissions are changed BEFORE Xorg is started.

---

### Post by jeremy31 on 2016-03-31
Might want to do a bug report, see [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

Only one other thing I can think of, put a piece of dark tape across the camera and see if this is some built in adaptive contrast

---

### Post by qrees on 2016-03-31
> **jeremy31 said:**
> Only one other thing I can think of, put a piece of dark tape across the camera and see if this is some built in adaptive contrast
Tried that :(

---

### Post by qrees on 2016-04-03
I've found a workaround.

Xorg has found multiple input devices, two of which are named: "Video Bus". Running "evtest" gives the following result:

```
/dev/input/event0:	Lid Switch
/dev/input/event1:	Sleep Button
/dev/input/event2:	Power Button
/dev/input/event3:	Power Button
/dev/input/event4:	AT Translated Set 2 keyboard
/dev/input/event5:	Video Bus
/dev/input/event6:	Video Bus
/dev/input/event7:	Logitech USB Receiver
...

```
So Xorg attaches "Video Bus" as keyboard input and Video Bus for some reason sends Brightness Up and Brightness Down events randomly.

Adding following section to "/usr/share/X11/xorg.conf.d/10-quirks.conf" :

```
Section "InputClass"
        Identifier "Spooky Ghosts"
        MatchProduct "Video Bus"
        Option "Ignore" "on"
EndSection

```
Solves the problem.

Also running "sensors" no longer results in random brightness changes.

---

### Post by Frederick888 on 2016-08-07
> **qrees said:**
> I've found a workaround.

Xorg has found multiple input devices, two of which are named: "Video Bus". Running "evtest" gives the following result:

```
/dev/input/event0:    Lid Switch
/dev/input/event1:    Sleep Button
/dev/input/event2:    Power Button
/dev/input/event3:    Power Button
/dev/input/event4:    AT Translated Set 2 keyboard
/dev/input/event5:    Video Bus
/dev/input/event6:    Video Bus
/dev/input/event7:    Logitech USB Receiver
...

```
So Xorg attaches "Video Bus" as keyboard input and Video Bus for some reason sends Brightness Up and Brightness Down events randomly.

Adding following section to "/usr/share/X11/xorg.conf.d/10-quirks.conf" :

```
Section "InputClass"
        Identifier "Spooky Ghosts"
        MatchProduct "Video Bus"
        Option "Ignore" "on"
EndSection

```
Solves the problem.

Also running "sensors" no longer results in random brightness changes.

PERFECT!

I've got two MSI laptops (16F2 & GT72S) and they both suffer from this issue under Kubuntu 16.04. This solution solved it on my GT72S and I'll try it later on 16F2. Many thanks.

---

