---
title: "XUbuntu Brightness Stuck on Max"
date: 2015-05-16
forum: General Help
---

### Post by randy24 on 2015-05-16
Hi everyone! After a frustrating series of events that led me to do fresh re-installs of Xubuntu three times (i'm new to linux), I have been able to fix all of my issues except one. My brightness is stuck on max and I cant change it. When i try to change the brightness, the slider moves fine but the brightness doesn't change at all. It stays at max.

Here's what I have tried:
1) I tried installing the brightness plugin for xfce-4 and placing in my panel. The slider doesn't work either. 
2) I tried updating my grub file to [COLOR=#3F4549][FONT=Georgia]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor" [/FONT][/COLOR]and it didn't work.

If anyone could help me get this issue sorted out asap, that would be very much appreciated. The brightness is starting to bother me when I work at night. Thank you!

---

### Post by RobGoss on 2015-05-16
Hello and welcome to the forum, I found this thread it might help you with your problem. [http://askubuntu.com/questions/296139/screen-brightness-stuck-on-max-setting-fndown-only-brings-it-down-one-level](http://askubuntu.com/questions/296139/screen-brightness-stuck-on-max-setting-fndown-only-brings-it-down-one-level)

---

### Post by randy24 on 2015-05-16
I tried those and it didn't work :/

---

### Post by Toz on 2015-05-16
Can you post back the following information (where required, open a terminal window, run the command, and post back the results):

1. The version of Xubuntu that you are using.

2. Your current kernel boot line:
```
cat /proc/cmdline
```

3. Information about your video card(s):
```
lspci -k | grep -iA2 VGA
```

4. Information about your known backlight interfaces:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```

5. A listing of your loaded kernel modules:
```
lsmod
```

6. Your /var/log/Xorg.0.log file:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

---

### Post by randy24 on 2015-05-17
Hi Toz! Thank you for replying

1) 14.04.02 LTS
2) BOOT_IMAGE=/boot/vmlinuz-3.13.0-52-generic.efi.signed root=UUID=e535c17c-10cb-4dae-ac3e-34f998ebfd09 ro "acpi_osi=!Windows 2012" quiet splash vt.handoff=7
3)01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 750M] (rev a1)	Subsystem: Lenovo Device 3800
	Kernel driver in use: nvidia
4) /sys/class/backlight/acpi_video0
15
15
15
5)Module                  Size  Used by
ctr                    13049  2 
ccm                    17773  2 
rfcomm                 69160  12 
bnep                   19624  2 
nls_iso8859_1          12713  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
arc4                   12608  2 
iwldvm                232285  0 
mac80211              630669  1 iwldvm
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_realtek    65580  1 
mxm_wmi                13021  0 
snd_hda_intel          56531  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
coretemp               13435  0 
kvm_intel             143187  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
kvm                   455835  1 kvm_intel
crct10dif_pclmul       14289  0 
snd_seq_midi           13324  0 
crc32_pclmul           13113  0 
snd_seq_midi_event     14899  1 snd_seq_midi
ghash_clmulni_intel    13216  0 
aesni_intel            55624  4 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_rawmidi            30144  1 snd_seq_midi
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
iwlwifi               169932  1 iwldvm
joydev                 17381  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
serio_raw              13462  0 
snd_timer              29482  2 snd_pcm,snd_seq
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
lpc_ich                21080  0 
btusb                  32412  0 
bluetooth             391136  22 bnep,btusb,rfcomm
nvidia               8379426  76 
mei_me                 18627  0 
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
mei                    82276  1 mei_me
drm                   303102  4 nvidia
soundcore              12680  1 snd
ideapad_laptop         18216  0 
sparse_keymap          13948  1 ideapad_laptop
parport_pc             32701  0 
ppdev                  17671  0 
shpchp                 37032  0 
wmi                    19177  1 mxm_wmi
lp                     17759  0 
video                  19476  0 
parport                42348  3 lp,ppdev,parport_pc
mac_hid                13205  0 
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  2 hid_generic,usbhid
psmouse               106714  0 
alx                    32452  0 
ahci                   29915  3 
libahci                32716  1 ahci
mdio                   13807  1 alx
6)[http://paste.ubuntu.com/11178962/](http://paste.ubuntu.com/11178962/)

Hope this helps!

---

### Post by Toz on 2015-05-17
Can you try creating the file **/usr/share/X11/xorg.conf.d/20-nvidia-brightness.conf** (as root):
```
gksudo mousepad  /usr/share/X11/xorg.conf.d/20-nvidia-brightness.conf
```
...with the following content:
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 750M"
    Option         "RegistryDwords" "EnableBrightnessControl=1"
EndSection
```

Save the file and log out and back in again to see if it makes a difference.

---

### Post by randy24 on 2015-05-17
I tried that and it still doesn't work :(

---

### Post by Toz on 2015-05-17
Can you post back the contents of the /usr/share/X11/xorg.conf.d/20-nvidia-brightness.conf file (to confirm) as well as another pastebinit of your /var/log/Xorg.0.log file?

What is the make and model of your computer?

And finally, can you remove the "acpi_osi=!Windows 2012" kernel parameter (make sure you run 'sudo update-grub'), reboot and post back the results of the same commands from post #4? Lets see what it looks like in its default state.

EDIT: Does xbacklight work?
```
xbacklight -dec 10
xbacklight -inc 10
```

---

### Post by randy24 on 2015-05-18
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GT 750M"
    Option         "RegistryDwords" "EnableBrightnessControl=1"
EndSection

My model is Lenovo 510p

2) BOOT_IMAGE=/boot/vmlinuz-3.13.0-52-generic.efi.signed root=UUID=e535c17c-10cb-4dae-ac3e-34f998ebfd09 ro quiet splash vt.handoff=7


[COLOR=#000000]
3) [/COLOR]01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 750M] (rev a1)	Subsystem: Lenovo Device 3800
	Kernel driver in use: nvidia


[COLOR=#000000]4) [/COLOR]88
100
88


[COLOR=#000000]5) [/COLOR]Module                  Size  Used by
ctr                    13049  2 
ccm                    17773  2 
rfcomm                 69160  12 
bnep                   19624  2 
nls_iso8859_1          12713  1 
uvcvideo               80885  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         40664  1 uvcvideo
videodev              134688  2 uvcvideo,videobuf2_core
arc4                   12608  2 
iwldvm                232285  0 
mac80211              630669  1 iwldvm
snd_hda_codec_hdmi     46368  1 
snd_hda_codec_realtek    65580  1 
mxm_wmi                13021  0 
snd_hda_intel          56531  5 
snd_hda_codec         192906  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm               102099  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       14705  0 
coretemp               13435  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
kvm_intel             143187  0 
kvm                   455835  1 kvm_intel
snd_seq_midi           13324  0 
crct10dif_pclmul       14289  0 
snd_seq_midi_event     14899  1 snd_seq_midi
crc32_pclmul           13113  0 
snd_rawmidi            30144  1 snd_seq_midi
ghash_clmulni_intel    13216  0 
aesni_intel            55624  4 
parport_pc             32701  0 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
ppdev                  17671  0 
snd_timer              29482  2 snd_pcm,snd_seq
iwlwifi               169932  1 iwldvm
joydev                 17381  0 
lp                     17759  0 
snd                    69322  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
parport                42348  3 lp,ppdev,parport_pc
serio_raw              13462  0 
btusb                  32412  0 
cfg80211              484040  3 iwlwifi,mac80211,iwldvm
bluetooth             391136  22 bnep,btusb,rfcomm
lpc_ich                21080  0 
ideapad_laptop         18216  0 
sparse_keymap          13948  1 ideapad_laptop
nvidia               8379426  76 
drm                   303102  4 nvidia
video                  19476  0 
wmi                    19177  1 mxm_wmi
soundcore              12680  1 snd
mac_hid                13205  0 
mei_me                 18627  0 
mei                    82276  1 mei_me
shpchp                 37032  0 
hid_generic            12548  0 
usbhid                 52659  0 
hid                   106148  2 hid_generic,usbhid
ahci                   29915  3 
psmouse               106714  0 
alx                    32452  0 
libahci                32716  1 ahci
mdio                   13807  1 alx


[COLOR=#000000]6) [/COLOR]http://paste.ubuntu.com/11200048/



NOTE: xbacklight -dec 10 and xbacklight -inc 10 both work after i installed xbacklight! First time i was able to change my brightness

---

### Post by Toz on 2015-05-18
> **randy24 said:**
> 
My model is Lenovo 510p
> NOTE: xbacklight -dec 10 and xbacklight -inc 10 both work after i installed xbacklight! First time i was able to change my brightness
I recall trying to help another person (see: [http://ubuntuforums.org/showthread.php?t=2167180]("http://ubuntuforums.org/showthread.php?t=2167180")) with the same notebook, and the only way to get it to work was to use xbacklight. The user in that thread ended up mapping xbacklight to keyboard shortcuts. There is also [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1258058]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1258058") existing bug report.

---

### Post by randy24 on 2015-05-18
Thank you very much Toz! I'm very glad we found a way to change the brightness. I'll look over the thread that you linked me and set up some shortcuts for myself! :)

---

