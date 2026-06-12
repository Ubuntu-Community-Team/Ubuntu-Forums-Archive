---
title: "xfce-power-manager - does not dim screen"
date: 2014-02-28
forum: General Help
---

### Post by Psil0cybin on 2014-02-28
Hello guys, 

I am using a new Lenovo G700 Laptop, I have set settings to dim the screen when my laptop is inactive for 15 seconds (within xfce-power-manager) this usually works for all my laptops/ all 2 except this one, yet my screen continues to glare at full brightness.
What can I do in order to diagnose this issue, find out if it is a bug? If there is a fix, etc?

Thank you in advance,
Psil0

---

### Post by Toz on 2014-02-28
Are you able to adjust your screen brightness using your keyboard controls, or is screen brightness basically non-functional?

Can you also post back the results of these commands so that we can have a closer look at your system?
```
cat /proc/cmdline
lspci -k | grep -iA2 VGA
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
lsmod

```

---

### Post by Psil0cybin on 2014-03-01
> Can you also post back the results of these commands so that we can have a closer look at your system?

I would love to, here are the outputs as specified. 

```
lspci -k | grep -iA2 VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
    Subsystem: Lenovo Device 3977
    Kernel driver in use: i915
 for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done

 /sys/class/backlight/acpi_video0
7
10
7

 /sys/class/backlight/intel_backlight
4882
4882
1301


```

and

```
BOOT_IMAGE=/boot/vmlinuz-3.2.0-59-generic root=UUID=5445fbf6-d7d5-4378-8ac7-69264731dcfb ro quiet splash acpi_osi=Linux vt.handoff=7


```

the hotkeys work perfectly fine, the keyboard function keys work fine as well, it seems to just be a dimming issue. (no other graphical issues - that I can notice - as of yet)

[B]_Note:_
[/B]I set acpi_osi=Linux in order to get the back light to start up by default, by standard vanilla install, backlight is turned off on boot (I need to use my keys to activate the backlight) Removing acpi_osi=Linux does not fix the issue. *Just thought I would note this, as I did change this personally...in case you might find it odd, etc..* It seems to not be a grub configuration but perhaps a bug? Or perhaps a setting configuration else where? I would really love to understand why this is happening, also what is the best way in order to go about learning how to solve issues such as this one in the future. 

also I do not know if I noted this before, but I am using_* Xubuntu 12.04 LTS.*_

[B]_Silly Careless Fact:_
[/B]I posted the commands you specified as is, into the terminal. If a command was missed, let me know and I will gladly repost anything that did not get outputted. :rolleyes:

****

---

### Post by Toz on 2014-03-01
The only thing that I can think of is that the power manager is getting confused by the two backlight interfaces. Try adding the **acpi_backlight=vendor** kernel parameter. This will remove the acpi_video0 interface leaving only the intel_backlight one and maybe removing the confusion.

EDIT: Also post back:
```
xfce4-power-manager --dump
```

---

### Post by Psil0cybin on 2014-03-01
Thank you so much for your quick replies/taking the time to help me attempt to diagnose this issue/problem

I am going to try your first suggestion in a second, I suspect I add that into the grub as I did with the acpi_os option. 

**Result of first command: **The command you specified did not work, but I did add it along side with acpi_os=Linux (dim setting does not work regardless of what I set it to)

**Just so we are on the same page: **My grub file looks like this, in case you are wondering what I did.. (Of course running "sudo grub-update" afterwards)

```
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux acpi_backlight=vendor"
```

Here is the output of the dump as you have suggested: 

```

---------------------------------------------------
       Xfce power manager version 1.0.11
With policykit support
With network manager support
With DPMS support
---------------------------------------------------
Can suspend: True
Can hibernate: True
Can spin down hard disks: True
Authorized to suspend: True
Authorized to hibernate: False
Authorized to shutdown: True
Authorized to spin down hard disks: True
Has battery: True
Has brightness panel: True
Has power button: True
Has hibernate button: True
Has sleep button: True
Has LID: True


```

I really hope I can get this dim feature working on this laptop :) that would really help me save my laptop battery life. I personally always forget to dim my screen using the hot keys when I go away for a quick couple of minutes.
If you can not suggest anything else, how would I go about filling a proper bug report for this in order to attempt to solve this issue properly? I know someone on IRC offered to help me with a PPA, but I do not like adding PPA's, they cause problems in the future. The individual did state that this was perhaps a bug that was fixed with a newer version of Xubuntu, but it is wierd that this works for every other laptop but this one. 

I am just a tad confused as this seems to be the only graphical issue i can notice when it comes to using this laptop, everything else is working fine when it comes to the graphical end (using transparencies, etc)
So are you suggesting this is strictly a software issue? Or could this be a hard ware issue (*which I do doubt)

*This problem seems to only affect my Lenovo G700 Laptop. Every other laptop I use is able to dim perfectly on idle. *

I have also attempted to post this problem on launchpad [ [https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1286446](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1286446) ] in order to attempt to speed up the process, I do not know if I am going about reporting bugs the right way.

Psil0

---

### Post by Toz on 2014-03-02
With the acpi_backlight=vendor parameter active, what are the results of this command again:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```

Which kernel modules are running:
```
lsmod
```

---

### Post by Psil0cybin on 2014-03-04
> **Toz said:**
> With the acpi_backlight=vendor parameter active, what are the results of this command again:
```
for interface in /sys/class/backlight/*; do echo -e "\n  $interface"; cat  $interface/{brightness,max_brightness,actual_brightness}; done
```

Which kernel modules are running:
```
lsmod
```

I will run the command in grub and post back the outputs, give me a second.
[B]
EDIT / RESULT: [/B]
Running the first command yields 

```

 /sys/class/backlight/ideapad
0
10
0

 /sys/class/backlight/intel_backlight
1954
4882
1954


```

The second command states

```

Module                  Size  Used by
dm_crypt               23125  1 
snd_hda_codec_hdmi     32530  1 
snd_hda_codec_idt      70795  0 
snd_hda_intel          33719  4 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12529  2 
ath9k                 132428  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
joydev                 17693  0 
mac80211              506862  1 ath9k
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    79041  18 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               72627  0 
ath9k_common           14053  1 ath9k
ath9k_hw              411239  2 ath9k,ath9k_common
videodev               98259  1 uvcvideo
parport_pc             32866  0 
mac_hid                13253  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
bnep                   18281  2 
psmouse                97519  0 
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
v4l2_compat_ioctl32    17128  1 videodev
cfg80211              205774  3 ath9k,mac80211,ath
rfcomm                 47604  0 
ppdev                  17113  0 
bluetooth             180113  10 bnep,rfcomm
ideapad_laptop         18234  0 
lp                     17799  0 
mei                    41616  0 
sparse_keymap          13890  1 ideapad_laptop
serio_raw              13211  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            49198  0 
wmi                    19256  0 
i915                  478556  2 
drm_kms_helper         46978  1 i915
drm                   241971  3 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19651  1 i915

```

Thank you so much for your help at the moment, :) I really hope we can get down to the bottom of this issue, and perhaps diagnose it...
I was thinking though, could this be caused by my other setting of acpsi_os=Linux? perhaps? The only difference I notice using your setting is that the hotkeys do not work for the first few minutes, and it adds much more options in order to add backlight like if I increase it instead of there being 4 settings, there are now 7. Sigh...

If this in fact not working, could we file a proper bug report or notify the right individuals? I am unfamiliar with submitting bug reports for problems that do not cause crashes.

---

### Post by Toz on 2014-03-04
With the acpi_backlight=vendor kernel parameter, you again get 2 backlight interfaces (intel_backlight and ideapad). You're on the right track with the [bug report]("https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1286446") you created - wait to see if you get some action there.

One other thing to note, the G700 is a relatively new laptop, and the kernel/Xorg versions with 12.04 are older. You may have more luck (and definitely more options) with a newer version of Ubuntu (with updated kernel/Xorg components). To investigate, I would suggest booting with a live cd/usb of 13.10 or even 14.04 beta to see if you get better support for backlight and dimming. There are also a number of other configuration options we can try such as the **acpi_osi='!Windows 2012'** kernel parameter and forcing the use of the intel_backlight interface through an xorg configuration hack. Both can be tried with the live cd so no changes need to be made on your current system.

---

### Post by Psil0cybin on 2014-03-12
> **Toz said:**
> With the acpi_backlight=vendor kernel parameter, you again get 2 backlight interfaces (intel_backlight and ideapad). You're on the right track with the [bug report]("https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1286446") you created - wait to see if you get some action there.

One other thing to note, the G700 is a relatively new laptop, and the kernel/Xorg versions with 12.04 are older. You may have more luck (and definitely more options) with a newer version of Ubuntu (with updated kernel/Xorg components). To investigate, I would suggest booting with a live cd/usb of 13.10 or even 14.04 beta to see if you get better support for backlight and dimming. There are also a number of other configuration options we can try such as the **acpi_osi='!Windows 2012'** kernel parameter and forcing the use of the intel_backlight interface through an xorg configuration hack. Both can be tried with the live cd so no changes need to be made on your current system.


Alright thank you so much for your advice, I will attempt the stuff you have outlined, I guess i will just have to wait and hope that popularity for the laptop I just got gains, hoping for a official fix for this issue. 
I was wondering if the fix's listed here might be able to help me, would you know?

[https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1067749](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1067749)

So I am assuming that we have exausted all other ideas?

---

### Post by Toz on 2014-03-12
> **Psil0cybin said:**
> 
I was wondering if the fix's listed here might be able to help me, would you know?
[https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1067749](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1067749)
These fixes are included in the latest versions of Xfce that are part of the release for 14.04. I would still recommend trying a live CD/USB of 14.04 to see if you get better backlight management.

> So I am assuming that we have exausted all other ideas?
I'm afraid that I have no other suggestions. I believe that you will have more luck with newer kernel/Xorg versions.

---

