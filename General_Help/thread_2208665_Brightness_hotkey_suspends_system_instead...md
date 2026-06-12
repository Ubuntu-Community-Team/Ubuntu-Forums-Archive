---
title: "Brightness hotkey suspends system instead.."
date: 2014-03-01
forum: General Help
---

### Post by omar-ahafez87 on 2014-03-01
Hello all,

I have just installed Ubuntu 13.10 on my Toshiba Satellite, AMD 64bit processor. Unfortunately, however there's a bunch of annoying problems.

One of these problems has to do with the laptop hotkeys for increasing and decreasing brightness. While the "decrease brightness" button does not work at all, the "increace button" sends the system to sleep/suspend instead. I am really not sure what I should do about this.

I tried to use th xev and xmodmap commands to remap the button, but I didn't know how to do it, and it probably does not work.

What can I do? And is there any other info you need to know to be able to help me?
And how do I get them for you?

Thank you very much.

---

### Post by varunendra on 2014-03-03
Welcome to the forums Omar!

The Fn key in Notebooks can't be captured with xev or any key-capture program I know of, so that is not going to help. We may try to look at other possibilities.

Please open a terminal (Ctrl-Alt-T) and run the following commands (you may copy-paste) -
```
uname -mr
lsmod
cat /proc/cmdline
for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done
```
Post back the outputs of the commands in your next post.

These will tell us the kernel version, the drivers that are loaded, custom boot parameters if you used any, and your screen backlight settings.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by IvoGuerreiro on 2014-03-03
I have a friend that had a similar problem and he had solved this way (not the best solution):


1- Click on the search bar and type "Settings" and Open the "System Settings".
2- Open the "Keyboard Shortcuts" tool.
3- Scroll through the list of shortcuts to find the operation associated with your key.
4- Click the "Shortcut" column of the operation you want to flip and press the function key you want to be the default.


As i had said, no perfect solution, so i will keep attention to this topic, perhaps i can help my friend.

---

### Post by omar-ahafez87 on 2014-03-03
Hi Varunendra,

Well, the thing is, I don't really need to use the FN key here. These functions work without it. It is when I want to use the button as an "Fx" (e.g. F1, F2.. etc.) that I need to use the FN key.
I am actually lucky in this respect.

I was able to find the keycodes, however, by using the xev event tester, and I press Alt + the button I want to find the keycode for.

In any case, here are the outputs you asked for:

```


omar@omar-Leipzig:~$ uname -mr
3.11.0-17-generic x86_64
----------

omar@omar-Leipzig:~$ lsmod
Module                  Size  Used by
joydev                 17377  0 
hid_generic            12548  0 
usbhid                 53014  0 
hid                   101762  3 hid_generic,usbhid
vesafb                 13828  1 
btusb                  28267  0 
uvcvideo               80885  0 
amd_freq_sensitivity    12589  0 
kvm_amd                59987  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
arc4                   12608  2 
snd_hda_codec_realtek    56405  1 
snd_hda_codec_hdmi     41117  1 
kvm                   431720  1 kvm_amd
snd_hda_intel          52267  5 
ath9k                 155779  0 
videobuf2_core         40499  1 uvcvideo
ath9k_common           13859  1 ath9k
snd_hda_codec         188738  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
ath9k_hw              444732  2 ath9k_common,ath9k
videodev              133509  2 uvcvideo,videobuf2_core
fglrx                6732964  1160 
crct10dif_pclmul       14289  0 
crc32_pclmul           13113  0 
ghash_clmulni_intel    13259  0 
snd_hwdep              13602  1 snd_hda_codec
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              597268  1 ath9k
snd_pcm               102033  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
aesni_intel            55624  1 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30095  1 snd_seq_midi
bnep                   19704  2 
rfcomm                 69130  12 
snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
cfg80211              480503  3 ath,ath9k,mac80211
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29433  2 snd_pcm,snd_seq
bluetooth             372041  22 bnep,btusb,rfcomm
snd                    69141  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
psmouse                97655  0 
edac_core              62342  0 
fam15h_power           13119  0 
microcode              23656  0 
k10temp                13126  0 
toshiba_acpi           22901  0 
serio_raw              13413  0 
edac_mce_amd           22617  0 
sparse_keymap          13948  1 toshiba_acpi
wmi                    19070  1 toshiba_acpi
soundcore              12680  1 snd
toshiba_bluetooth      12852  0 
i2c_piix4              22106  0 
amd_iommu_v2           19054  1 fglrx
video                  19318  0 
mac_hid                13205  0 
parport_pc             32701  0 
ppdev                  17671  0 
lp                     17759  0 
parport                42299  3 lp,ppdev,parport_pc
ahci                   25819  2 
r8169                  67581  0 
libahci                32009  1 ahci
mii                    13934  1 r8169

------------------

omar@omar-Leipzig:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.11.0-17-generic root=UUID=9ad68141-b003-4fd8-8f8c-5eb605f338b5 ro nomodeset

------------------

omar@omar-Leipzig:~$ for i in /sys/class/backlight/*; do echo -e "\n $i"; cat $i/{brightness,max_brightness,actual_brightness}; done

 /sys/class/backlight/acpi_video0
100
100
100




```

---

### Post by varunendra on 2014-03-04
Were you able to map the keys to meet your requirements then? If so, please consider marking the thread as [SOLVED] (using "Thread Tools" link above the first post).

If you are still unable to control the brightness, we may try a few things to make it happen naturally. If not, we can try to manually control it via a script and bind it with a hot key as a workaround to offer same/similar functionality. Your current brightness seems to be at maximum.

---

### Post by omar-ahafez87 on 2014-03-04
I was actually able to remap the key with xmodmap, but the remapping wil go away as soon as the system resumes from sleep (or reboot, or thaw of course).

I was thinking of actually using the following script in /etc/pm/sleep.d to have the xmodmap excute at every resume:

```
 

#!/bin/bash

case "$1" in
   hibernate|suspend) ;;
   thaw|resume)
         echo "It works!" >> /home/omarkeysscript.log
         sudo -u  omar env DISPLAY=:0 xmodmap -e "keycode 150 = XF86MonBrightnessUp"
         sudo -u  omar env DISPLAY=:0 xmodmap -e "keycode 244  mod2 = XF86MonBrightnessDown"

         ;;


esac

exit $?


```

But to no avail. The script does not seem to work as desired. Of course I named it *000Zbrightnesskeys* to insure it is the last script to excute, but it didn't work.

---

### Post by varunendra on 2014-03-04
The scripts in /etc/.. directory are already run as root, you don't have to use 'sudo' with them.

Alternatively, you may try to 'echo' desired brightness values to your /sys/class/backlight/acpi_video0/brightness file using a custom script, and use something like 'xbindkeys' to bind a pair of hotkeys to run that script with a desired hotkey. Let me know if you need help with such workaround, I've done it in past and is quite simple. But your approach seems better, if it works after removing the 'sudo', or improvising it if required.

---

### Post by omar-ahafez87 on 2014-03-05
Actually, it turns out that almost all the buttons are messed up. 
The Display(or switch monitors) button also suspends the computer.
The Wireless button is not assigned.. and so on.

This is very disturbing to be honest with you.

Do you think that maybe if I reinstall Ubuntu that this might be fixed, or am I still going to get the same problem?

Thank you for your help.

---

### Post by varunendra on 2014-03-05
That is most probably a problem with the "toshiba_acpi" module not being able to handle the hotkeys. I've seen such problems with some Toshiba models, especially new ones, but I don't yet know of a promising fix or workaround.

The only thing I may suggest is to try blacklisting the "toshiba_acpi" module and see if anything improves (things may also get worse with it blacklisted, so keep a live cd/usb handy).

If that doesn't help, file a bug report at launchpad and hope for a fix or pointers to a fix/workaround. A handy tool to collect information for the bug report -
```
apport-bug
```

In the meanwhile, you may try yourself a few kernel options that may sometimes magically fix such issues. Especially try those that are related to "acpi" : [https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options)

An exhaustive list of kernel options is also given at the bottom of the above linked page, but I doubt a normal user would ever want to go that far.

---

### Post by omar-ahafez87 on 2014-03-09
To keep this thread up-to-date, I just realized that this is not just an Ubuntu problem. The very same issue appeared when I used Fedora 20 in Live version.

It's apparently either an issue with my model of Toshiba Satellite, or with the Linux kernel itself...

---

### Post by coleman_ian on 2014-04-09
I have been digging into this myself and have posted about it at [http://bit.ly/1lPnTar](http://bit.ly/1lPnTar) - apologies for the url shortner but the real one contains the f word and was being mangled by the auto-censored on this forum.

The main info I concluded is that the brightness up/down keys are being detected incorrectly as acpi events.

```
$ acpi_listen
Brightness down (Fn-F2):
button/battery BAT 00000080 00000000 K
Brightness up (Fn-F3):
button/sleep SBTN 00000080 00000000 K
```

---

