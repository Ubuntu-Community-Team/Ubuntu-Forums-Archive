---
title: "Asus Zenbook UX303 Problems"
date: 2014-09-06
forum: General Help
---

### Post by Maheriano on 2014-09-06
I just bought the newest Zenbook and it doesn't seem to be cooperating well with Ubuntu 14.04. The biggest issue with it is the track pad, I can't get anything out of it except single touch and click. I'd like the following:
- 2 finger click = right click
- 2 finger scrolling

Any idea how I can get these to work? I'm thinking about bringing this one back and getting the Samsung Ativ Book 9 if this won't cooperate.

---

### Post by gordintoronto on 2014-09-07
Quite often, it takes a little while before the latest hardware is fully supported by Linux. I have no insight into the specifics of your desires.

Have you tried scrolling using the right edge of the trackpad?

---

### Post by Maheriano on 2014-09-08
I have tried that, nothing is working.

---

### Post by coleifer on 2014-09-19
I just created an account so I could reply. I just bought a UX303 and installed Arch on it. I'm experiencing the same problems with the trackpad (kernel version 3.16.3-1).

I've tried everything in this list: [https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Touchpad_detected_as_.22PS.2F2_Generic_Mouse.22_or_.22Logitech_PS.2F2_mouse.22](https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Touchpad_detected_as_.22PS.2F2_Generic_Mouse.22_or_.22Logitech_PS.2F2_mouse.22)

No luck-- still just getting recognized as a generic ps/2 mouse. There's an absolute dearth of useful information out there on this model -- probably going to end up returning it.

---

### Post by branoic on 2014-09-21
Hi!

I am having the exact same problem with mine too. There's only single click working here.
Apart from the trackpad I only have problem with using the buttons for increasing / decreasing the brightness on the screen.

Have you tried or found any solution to the problem?

---

### Post by courvilb on 2014-09-22
I just wanted to report that I am experiencing similar issues with trackpad and screen brightness buttons.

I tried the fixes for previous zenbooks [https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime) and [https://help.ubuntu.com/community/AsusZenbook](https://help.ubuntu.com/community/AsusZenbook) but was unable to find a solution.

---

### Post by guillaume-desclaux on 2014-09-22
> **branoic said:**
> Hi!

I am having the exact same problem with mine too. There's only single click working here.
Apart from the trackpad I only have problem with using the buttons for increasing / decreasing the brightness on the screen.

Have you tried or found any solution to the problem?
To solve the brightness buttons problem, you have to add the option acpi_osi without value in your /etc/default/grub file like this :

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

and then : update-grub

---

### Post by courvilb on 2014-09-22
> **guillaume-desclaux said:**
> To solve the brightness buttons problem, you have to add the option acpi_osi without value in your /etc/default/grub file like this :

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

and then : update-grub

Thanks! I can confirm this worked for me. Now the only issue is the trackpad.

---

### Post by denis27 on 2014-09-23
Hi guys, thanks for the brightness tip :)

I have the same issue on the touchpad, it looks like it's not even detected by the system.

```

$> xinput list
&#9121; Virtual core pointer                          id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                id=4    [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® Nano Transceiver v2.0        id=11   [slave  pointer  (2)]
&#9116;   &#8627; Microsoft Microsoft® Nano Transceiver v2.0        id=12   [slave  pointer  (2)]
&#9116;   &#8627; Atmel Atmel maXTouch Digitizer            id=14   [slave  pointer  (2)]
&#9116;   &#8627; PS/2 Logitech Wheel Mouse                 id=17   [slave  pointer  (2)]
&#9123; Virtual core keyboard                         id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard               id=5    [slave  keyboard (3)]
    &#8627; Power Button                              id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=7    [slave  keyboard (3)]
    &#8627; Video Bus                                 id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                              id=9    [slave  keyboard (3)]
    &#8627; Microsoft Microsoft® Nano Transceiver v2.0        id=10   [slave  keyboard (3)]
    &#8627; USB2.0 UVC HD Webcam                      id=13   [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                          id=15   [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard              id=16   [slave  keyboard (3)]

```

And

```

$>synclient -l
Couldn't find synaptics properties. No synaptics driver loaded?

```

I'm using Ubuntu Gnome 14.01.1 LTS with kernel 3.13.0-35-generic

Also, do you have any issue with the HiDPI screen?

---

### Post by guillaume-desclaux on 2014-09-23
By the way : Asus has just released today a Bios firmware update !

[http://dlcdnet.asus.com/pub/ASUS/nb/UX303LA/UX303LAAS204.zip](http://dlcdnet.asus.com/pub/ASUS/nb/UX303LA/UX303LAAS204.zip)

I've not installed it yet.

---

### Post by denis27 on 2014-09-25
Indeed, but nothing very interesting for us in the changelog :)

I also noticed a wifi speed problem what about you guys?

---

### Post by courvilb on 2014-09-25
Nothing interesting to report after updating the BIOS, wishful thinking on my part I guess.

---

### Post by CTrox on 2014-09-27
Someone filed a bug report for this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1372609](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1372609)

I really hope we can get the touchpad to work properly.

---

### Post by gubbins2 on 2014-09-29
Hi, I also just bought a Asus UX303LN. I made a Windows USB recovery drive and then reformatted the disk with a fresh Lubuntu install.

I have the same trackpad issues. My brightness keys now work, after following guillaume-desclaux's tip on this thread (thanks!)

More importantly, I can't get any audio to work! I didn't even notice initially as I never even thought to try it - but then I realised it was broken. So far I am just trying to get the inbuilt speakers to do something (no headphones or HDMI attempted yet).

Example:
```

> aplay /usr/share/sounds/alsa/Noise.wav
ALSA lib pcm_dmix.c:1022:(snd_pcm_dmix_open) unable to open slave
aplay: main:722: audio open error: No such file or directory

```
Same result with sudo. My username is in the audio group.

Similarly if I open Audacious, I get an error dialog that says "ALSA error: No suitable mixer element found. ALSA error:snd_mixer_find_selem failed."

If I run alsamixer, I can press F6 and select card 1 (HDA Intel PCH) and then I get what looks like a perfectly sensible mixer display...

Maheriano, clearly you didn't have this problem - any ideas what's different for you? Could the behaviour be different because I went with Lubuntu instead of Ubuntu?

The laptop was also a display model in the shop, and I did wonder whether they might have disabled the audio in the BIOS somehow. There is an option under Security to "Lock" the "HD Audio Interface", whatever that means, but it is set to UnLock.

Other info if useful:
```

> cat /proc/version
Linux version 3.13.0-36-generic (build@toyol) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014

> lspci | grep Audio
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)

> cat /proc/asound/cards
 0 [HDMI           ]: HDA-Intel - HDA Intel HDMI
                      HDA Intel HDMI at 0xf791c000 irq 65
 1 [PCM            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xf7918000 irq 64

> cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_hda_intel

> cat /proc/asound/card*/codec* | grep Codec
Codec: Intel Haswell HDMI
Codec: Conexant CX20751/2

```

...and some stuff in dmesg:
```

[    3.944934] hda_codec: CX20751/2: BIOS auto-probing.
[    3.945145] autoconfig: line_outs=1 (0x17/0x0/0x0/0x0/0x0) type:speaker
[    3.945147]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.945149]    hp_outs=1 (0x16/0x0/0x0/0x0/0x0)
[    3.945151]    mono: mono_out=0x0
[    3.945152]    inputs:
[    3.945154]      Internal Mic=0x1a
[    3.945156]      Mic=0x19
[    3.946292] hda_codec: Enable sync_write for stable communication

```

Below that there are some ACPI Warnings of the form "SystemIO conflicts with Region ...", "If an ACPI driver is available for this device, you should use it instead of the native driver"

---

### Post by gubbins2 on 2014-09-29
PS: I will try installing pulseaudio and pavucontrol tonight, based on what I see in this thread: [http://ubuntuforums.org/showthread.php?t=2032252](http://ubuntuforums.org/showthread.php?t=2032252)

---

### Post by gubbins2 on 2014-09-30
OK, installing pulseaudio and pavucontrol did indeed magically fix the audio. I don't understand exactly why, but, it's working :)  Evidently these come by default with Ubuntu but not Lubuntu.

Issues I am still having:
[LIST]
[*]Known trackpad issues (also I find it very hard to make a mouse click without moving the cursor!)
[*]WiFi connection is very unreliable, with the achieved bandwidth varying randomly from normal to almost zero; disabling power management on wlan0 seems to fix it, but on a reboot the power management is switched on again so I don't know how to make it permanent yet
[*]Volume keys are still non-functional, but I think that's Lubuntu-specific again - KeyTouch was not installed and I couldn't get it working, and there is no keyboard shortcut configuration in the default Lubuntu install that I can see...
[*]Keyboard backlight is not working - only the power and F2 keys are lit
[*]Power button randomly became non-functional some time this morning
[/LIST]

I have not tried the HDMI, nor the nvidia graphics, yet.

Given the above issues I think I will abandon Lubuntu and start again with a different flavour, maybe just plain Ubuntu.

---

### Post by denis27 on 2014-10-01
I'm on Ubuntu Gnome kernel 3.13.0-36-generic.

Issues I am still having:
[LIST]
[*]Known trackpad issues [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1372609](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1372609)
[*][COLOR=#000000]WiFi connection is very unreliable, and SLOW! I tried everything power management included and it didn't really fix the problem so I bought a Trendnet N150 (TEW-648UBM) which contain a Realtek chipset. I had to [do that to make it work]("https://sites.google.com/site/easylinuxtipsproject/reserve-7") but now it's like a just discover Internet again :)[/COLOR]
[*][COLOR=#000000][/COLOR][COLOR=#000000]Chromium and other applications are very "small" because of the HiDPI screen but I'm kind of used to it now.[/COLOR]
[/LIST]
[COLOR=#000000]
I wonder if we should create a specific bug report for the UX303 because there is already A LOT of report related to the Intel 7260 chipset, but it's a bit messy... What do you think guys?
[/COLOR]

---

### Post by m-bachmann on 2014-10-01
Could anyone test if output on 3 displays (internal + 2 external ones) works? 

I use my Zenbook 301 in this setup and it works perfectly (but my model has only intel graphics). I fear the Nvidia/Intel combo could pose a problem for a 3-display-setup. Any feedback greatly appreciated (I tried Asus support but did not get any useful information).

---

### Post by gubbins2 on 2014-10-01
I managed to disable the power management on the wifi by putting a script in /etc/pm/power.d, and it's been a lot better - but I guess an external adapter is not a terrible solution given that there are 3 USB ports...

denis27, did you get the keyboard fully working including the backlight...? I haven't managed that yet.

Would you believe I also noticed today that there is some image burn-in on my screen! On a dark grey background, I can (faintly) read the words "PASS 0 Day" and "... to Logout" in large font. Either some quality testing was left up too long, or it happened in the shop (serves me right for buying the display model). I am hoping that some scrubber screensaver will resolve it.

---

### Post by denis27 on 2014-10-02
gubbins2 yes everything is fine with my keyboard. I just had the brightness buttons issue but the post of guillaume-desclaux solved it!

> **guillaume-desclaux said:**
> To solve the brightness buttons problem, you have to add the option acpi_osi without value in your /etc/default/grub file like this :

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

and then : update-grub

---

### Post by gubbins2 on 2014-10-02
Wow, it's taking some work to get the special keys working. Evidently a lot of these work from a plain Ubuntu install, but not from Xubuntu/Lubuntu. Here's my roundup in case anyone else is trying to do this on Xubuntu... most of these can be controlled via the Application Shortcuts screen in the xfce Keyboard settings:
[LIST]
[*]Fn+F1 (sleep): detected as XF86Sleep; not mapped to anything yet
[*]Fn+F2 (airplane mode): detected as XF86WLAN; not mapped to anything yet
[*]Fn+F3/F4 (keyboard backlight brightness): I had to map these to my own shell scripts, which I got working following the excellent instructions here: [https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)
[*]Fn+F5/F6 (screen brightness): after applying the "acpi_os=" grub fix on this thread, these work fine
[*]Fn+F7 (screen off): worked out of the box
[*]Fn+F8 (display): detected as XF86Display; mapped to a display settings dialog by default
[*]Fn+F9 (touchpad toggle): detected as XF86TouchpadToggle; not mapped to anything yet
[*]Fn+F10/F11/F12 (volume): I had to map these to my own shell scripts, which use pacmd to control the volume; the xfce help has a screenshot showing them mapped to amixer commands ([FONT=arial]http://docs.xfce.org/xfce/xfce4-settings/keyboard[/FONT]) but I couldn't get amixer to work despite a lot of effort, possibly because pulseaudio is installed
[*]Fn+A (auto brightness): seems non-functional; not available to map in Application Shortcuts...
[/LIST]

I haven't even attempted external audio/video, let alone getting the nvidia hardware working properly...

---

### Post by mwingender on 2014-10-10
Hi all,
is there a way to modify the edges of the touchpad of the UX303LA? I understood that most touchpad features are currently not working. I would like to "exclude" the buttons from touch zone. It is a bit unhandy for me if mouse cursor moves when I want to hit the right or left button.

Br

---

### Post by guillaume-desclaux on 2014-11-04
To solve the touchpad issue, you should give a try to this custom kernel with Focaltech driver enabled ! A big Thanks for all the work done by these guys on this thread : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1372609](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1372609)  Keep up the good work !

Kernel with FocalTech support : [https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0](https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0)

---

### Post by simeurope on 2014-11-06
Many thanks !!!!
(i'm still testing but I'm afraid only 2 fingers gestures are recognized ?)


So what about configuring the touchscreen and the touchpad now ? ;)

I tried with Touchegg (just for the touchscreen, it was before guillaume's help) and it worked quite well.
However I'd prefer to use Ginn, but it doesn't seems to work for the moment (I didn't try very hard yet...).

My real question is : how can I configure different gestures for the touchscreen and the touchpad ?

---

### Post by Pilot6 on 2014-11-07
Up to 5 fingers are recognized by touchpad, but there are no out-of-the-box settings in Ubuntu to configure them.
But for instance if you run in terninal "synclient TapButton3=2" three finger tap will be set as a middle mouse click.
There are ways to set other gestures, but I do not really need them. In unity there are many hotkeys instead. 
If you press and hold Super (Win) button, you'll see them.

---

### Post by gubbins2 on 2014-11-08
> **guillaume-desclaux said:**
> To solve the touchpad issue, you should give a try to this custom kernel with Focaltech driver enabled ! A big Thanks for all the work done by these guys on this thread : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1372609](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1372609)  Keep up the good work !

Kernel with FocalTech support : [https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0](https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0)

Awesome news and many thanks to everyone who worked on that.

What's the likely timeline for this coming through in the regular Ubuntu updates? I am wondering whether to just wait for that.

---

### Post by Pilot6 on 2014-11-09
It won't be fast to get to an official Ubuntu kernel. Propbably after 15.04 is released unless they accept the backport patch. Either way a few months.

I suggest to use it now. You can always switch back, if something goes wrong.

---

### Post by gubbins2 on 2014-11-09
OK I will give it a go...

---

### Post by Pilot6 on 2014-11-09
If you do, please, give feedback.

---

### Post by gubbins2 on 2014-11-09
Well, I got some errors when installing the two packages:
```

> sudo dpkg -i linux-headers-3.16.4-focaltech-2+_3.16.4-focaltech-2+-10.00.Custom_amd64.deb linux-image-3.16.4-focaltech-2+_3.16.4-focaltech-2+-10.00.Custom_amd64.deb 
Selecting previously unselected package linux-headers-3.16.4-focaltech-2+.
(Reading database ... 203805 files and directories currently installed.)
Preparing to unpack linux-headers-3.16.4-focaltech-2+_3.16.4-focaltech-2+-10.00.Custom_amd64.deb ...
Unpacking linux-headers-3.16.4-focaltech-2+ (3.16.4-focaltech-2+-10.00.Custom) ...
Selecting previously unselected package linux-image-3.16.4-focaltech-2+.
Preparing to unpack linux-image-3.16.4-focaltech-2+_3.16.4-focaltech-2+-10.00.Custom_amd64.deb ...
Done.
Unpacking linux-image-3.16.4-focaltech-2+ (3.16.4-focaltech-2+-10.00.Custom) ...
Setting up linux-headers-3.16.4-focaltech-2+ (3.16.4-focaltech-2+-10.00.Custom) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.16.4-focaltech-2+ /boot/vmlinuz-3.16.4-focaltech-2+
Error! Your kernel headers for kernel 3.16.4-focaltech-2+ cannot be found.
Please install the linux-headers-3.16.4-focaltech-2+ package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.16.4-focaltech-2+ cannot be found.
Please install the linux-headers-3.16.4-focaltech-2+ package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.16.4-focaltech-2+ cannot be found.
Please install the linux-headers-3.16.4-focaltech-2+ package,
or use the --kernelsourcedir option to tell DKMS where it's located
Setting up linux-image-3.16.4-focaltech-2+ (3.16.4-focaltech-2+-10.00.Custom) ...


 Hmm. There is a symbolic link /lib/modules/3.16.4-focaltech-2+/build
 However, I can not read it: No such file or directory
 Therefore, I am deleting /lib/modules/3.16.4-focaltech-2+/build




 Hmm. The package shipped with a symbolic link /lib/modules/3.16.4-focaltech-2+/source
 However, I can not read the target: No such file or directory
 Therefore, I am deleting /lib/modules/3.16.4-focaltech-2+/source


Running depmod.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.4-focaltech-2+ /boot/vmlinuz-3.16.4-focaltech-2+
run-parts: executing /etc/kernel/postinst.d/dkms 3.16.4-focaltech-2+ /boot/vmlinuz-3.16.4-focaltech-2+
Error! Bad return status for module build on kernel: 3.16.4-focaltech-2+ (x86_64)
Consult /var/lib/dkms/nvidia-331-updates/331.38/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.4-focaltech-2+ /boot/vmlinuz-3.16.4-focaltech-2+
update-initramfs: Generating /boot/initrd.img-3.16.4-focaltech-2+
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.4-focaltech-2+ /boot/vmlinuz-3.16.4-focaltech-2+
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.4-focaltech-2+ /boot/vmlinuz-3.16.4-focaltech-2+
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.16.4-focaltech-2+ /boot/vmlinuz-3.16.4-focaltech-2+
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.16.4-focaltech-2+...
P: Writing config for /boot/vmlinuz-3.13.0-39-generic.efi.signed...
P: Writing config for /boot/vmlinuz-3.13.0-39-generic...
P: Writing config for /boot/vmlinuz-3.13.0-37-generic.efi.signed...
P: Writing config for /boot/vmlinuz-3.13.0-37-generic...
P: Updating /boot/extlinux/linux.cfg...
P: Installing debian theme... done.
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.4-focaltech-2+ /boot/vmlinuz-3.16.4-focaltech-2+
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.16.4-focaltech-2+
Found initrd image: /boot/initrd.img-3.16.4-focaltech-2+
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Adding boot menu entry for EFI firmware configuration
done

```

I also got a crash report about an nvidia module. Anyway after a reboot it seems to be working :)  Two-finger scrolling works nicely and I can see the device listed as a Focaltech in the XFCE keyboard and mouse settings. Great stuff. Now I am digging into the synaptics config options which I've never used before... can I get decent palm detection going? (It has been driving me nuts)

---

### Post by Pilot6 on 2014-11-09
This warning is OK. Don't worry.

You had problems with nvidia probably because you installed nvidia driver in a wrong way. Not from a repo, but from a .run file.
If you install it this way, then you have to reinstall it each time you update the kernel.
The better way is to install from official or unoffical repos.

Regarding palm detection. Palm detection is in hardware, but the problem is that accidental touches cannot be always detected.
You can test hardware palm detection by putting your palm on the touchpad firmly.

The problem is that in 14.04-14.10 "Disable touchpad while typing" option does not work. This is also a bug.
But it can easily be fixed by adding 

syndaemon -i 2 -tKd

command as an automatically started application. Not rc.local but in dash. It will turn off touchpad clicks for 2 seconds after you press a keyboard button.
You can change this time by -i parameter.

---

### Post by Pilot6 on 2014-11-09
In addition you can enable 3 finger tap as a middle mouse click by adding

synclient TapButton3=2

same way.

But it will be disabled after suspend/resume. I have a workaround for that too.

---

### Post by gubbins2 on 2014-11-09
The crash report was a failure to build the nvidia-331 module. I installed it originally (only a month or so ago...) like this:
apt-get install nvidia-331-updates
Should be OK, right?

Middle-mouse button worked out of the box, touchpad disable while typing works as configured in the settings GUI, and I have modified the palm detection settings via synclient to see how I get on. It's so nice to be able to click without moving the cursor...

---

### Post by Pilot6 on 2014-11-09
Maybe in xfce default behaviour is better that in unity. I had to enable 3 finger tap as it ignored xorg.conf.

But if nvidia driver works, then it must be OK. Did you check it?

---

### Post by gubbins2 on 2014-11-09
I think something broke:
> optirun glxgears 
[ 6227.821554] [ERROR]The Bumblebee daemon has not been started yet or the socket path /var/run/bumblebee.socket was incorrect.
[ 6227.821569] [ERROR]Could not connect to bumblebee daemon - is it running?
> bumblebeed
[ 6392.434047] [ERROR]Module 'nvidia-current' is not found.


This used to work fine

---

### Post by Pilot6 on 2014-11-09
I think the driver was not built.
Try to install it again.

sudo apt-get install --reinstall nvidia-331-updates

---

### Post by Pilot6 on 2014-11-10
I rebuilt kernel images for the latest 3.16 Uubntu kernel. Try them. It may solve nvidia problem.

---

### Post by simeurope on 2014-11-15
I tried to install the nvidia 331, but it doesn't work... maybe because I'm using the Focaltec ready kernel posted higher on this thread ?

I'm getting this :

mox@mox-UX303LN:~$ sudo apt-get install --reinstall nvidia-331-updates 

Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Les paquets suivants ont été installés automatiquement et ne sont plus nécessaires*:
  kde-l10n-engb kde-l10n-fr libbamf3-2 linux-image-3.16.0-23-generic linux-image-extra-3.16.0-23-generic linux-signed-image-3.16.0-23-generic thunderbird-locale-en thunderbird-locale-en-gb thunderbird-locale-en-us thunderbird-locale-fr
Veuillez utiliser «*apt-get autoremove*» pour les supprimer.
0 mis à jour, 0 nouvellement installés, 1 réinstallés, 0 à enlever et 19 non mis à jour.
Il est nécessaire de prendre 0 o/36,6 Mo dans les archives.
Après cette opération, 0 o d'espace disque supplémentaires seront utilisés.
debconf: Impossible d'initialiser l'interface*: Dialog
debconf: (L'interface dialog a besoin d'un écran d'au moins 13 lignes sur 31 colonnes.)
debconf: Utilisation de l'interface Readline en remplacement
(Lecture de la base de données... 312396 fichiers et répertoires déjà installés.)
Préparation du dépaquetage de .../nvidia-331-updates_331.89-0ubuntu5_amd64.deb ...
Removing all DKMS Modules
Done.
Dépaquetage de nvidia-331-updates (331.89-0ubuntu5) sur (331.89-0ubuntu5) ...
Traitement des actions différées («*triggers*») pour ureadahead (0.100.0-16)*...
ureadahead will be reprofiled on next reboot
Traitement des actions différées («*triggers*») pour man-db (2.7.0.2-2)*...
Paramétrage de nvidia-331-updates (331.89-0ubuntu5) ...
INFO:Enable nvidia-331-updates
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
Loading new nvidia-331-updates-331.89 DKMS files...
Building for 3.16.4-focaltech-2+ and 3.18.0-031800rc2-generic
Building for architecture x86_64
Building initial module for 3.16.4-focaltech-2+
ERROR (dkms apport): kernel package linux-headers-3.16.4-focaltech-2+ is not supported
Error! Bad return status for module build on kernel: 3.16.4-focaltech-2+ (x86_64)
Consult /var/lib/dkms/nvidia-331-updates/331.89/build/make.log for more information.

---

### Post by Pilot6 on 2014-11-16
It has nothing to do with the focaltech driver. It does not affect building of nvidia driver. The problem must be with the newer kernel itself.
In official repository installation script is for 3.13 kernel, not 3.16.

I suggest two things:

1. Install 3.16.7 kernel form the same URL I gave and reinstall nvidia driver.

```
sudo apt-get install --reinstall nvidia-331-updates
```

2. If the driver is not built again try to install the same driver from ppa using these commands.

```
sudo apt-get purge nvidia*
sudo add-apt-repository  ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-331
sudo add-apt-repository -r ppa:xorg-edgers/ppa

```
The driver should install OK.

---

### Post by denis27 on 2014-11-27
A fresh install of Ubuntu Gnome 14.04.1 fix my wifi problem. Now it's fast and stable without changing anything relied to the power management stuff.

---

### Post by gubbins2 on 2014-12-01
Thanks Pilot6 for the help - I am just returning to this today.

> **Pilot6 said:**
> I suggest two things:

1. Install 3.16.7 kernel form the same URL I gave and reinstall nvidia driver.


I see four .deb files in that dropbox, and they all say "3.16.0" (not 3.16.7) - sorry for being dumb but are you suggesting that we install all four of those 3.16.0 packages?

I also saw the README which suggested running a purge command first, and the purge command threw up a warning that I was removing the currently-active kernel package... I aborted that!

---

### Post by Pilot6 on 2014-12-01
Yes, you should install all 4 debs.

A little safer way is to boot from an official kernel first using grub, then remove 3.16.7 kernel.
It is needed to remove it, because the system loads with the highest kernel number by default.

---

### Post by gubbins2 on 2014-12-01
OK, good advice - I did that, installed the four packages you linked, reinstalled nvidia-updates-331, and this time it built fine. After another reboot, it looks like I have the trackpad and nvidia driver both working :D  That should help my battery life a bit.

Thanks so much for your help Pilot6.

---

### Post by Pilot6 on 2014-12-01
Good, that it helps. I will try too keep kernel up to date. Now you have installed 3.16.0-26 kernel. It will be next for update.
After 3.16.0-27 is out, I will replace debs.

---

### Post by denis27 on 2014-12-02
Pilot, since I've installed the 3.16 kernel, my wifi connection is going down very often (which wasn't the case on the official 3.13). Can we do something?

---

### Post by Pilot6 on 2014-12-02
> **denis27 said:**
> Pilot, since I've installed the 3.16 kernel, my wifi connection is going down very often (which wasn't the case on the official 3.13). Can we do something?
First of all remove 3.16.7 or 3.16.4 kernel, if you installed one of those. Then try the image, which is there now.
If the problem persists, then give output of

lspci -knn | grep Net -A2

---

### Post by denis27 on 2014-12-02
Same problem. Here is the output

```

02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
    Subsystem: Intel Corporation Dual Band Wireless-N 7260 [8086:c160]
    Kernel driver in use: iwlwifi

```

---

### Post by Pilot6 on 2014-12-02
I do not think it is a kernel regression. Please give output

uname -a

---

### Post by denis27 on 2014-12-02
```
Linux bruce-laptop 3.16.0-26-generic #35 SMP Tue Dec 2 18:59:07 MSK 2014 x86_64 x86_64 x86_64 GNU/Linux
```

And the one which runs well is linux-image-3.13.0-32-generic

---

### Post by Pilot6 on 2014-12-02
This is an official Ubuntu 3.16 kernel. I can't fix this if it is really driver related. 
Do you test both kernels at the same time? Boot with one, then boot with the other and test.
It may be just radio channel related.

---

### Post by denis27 on 2014-12-02
Running the 3.16

```

&#9786;  ~&#11136; speedtest
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from Orange (***)...
Selecting best server based on latency...
Hosted by iperf.fr (Rouen) [315.45 km]: 15.149 ms
Testing download speed........................................
Download: 19.17 Mbits/s
Testing upload speed..................................................
Upload: 30.53 Mbits/s

```

After reboot on the 3.13

```

&#9786;  ~&#11136; speedtest
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from Orange (***)...
Selecting best server based on latency...
Hosted by TestDebit.info (Limoges) [264.48 km]: 13.848 ms
Testing download speed........................................
Download: 61.95 Mbits/s
Testing upload speed..................................................
Upload: 71.33 Mbits/s

```

---

### Post by Pilot6 on 2014-12-02
Well, it may be a regression. You may install linux-generic-lts-utopic, wich is 100% official 3.16 kernel and make a bugreport to launchpad.

---

### Post by denis27 on 2014-12-02
Here is the bug report [https://bugs.launchpad.net/ubuntu/+source/linux-lts-utopic/+bug/1398585](https://bugs.launchpad.net/ubuntu/+source/linux-lts-utopic/+bug/1398585)

---

### Post by Pilot6 on 2014-12-02
> **denis27 said:**
> Here is the bug report [https://bugs.launchpad.net/ubuntu/+source/linux-lts-utopic/+bug/1398585](https://bugs.launchpad.net/ubuntu/+source/linux-lts-utopic/+bug/1398585)

You did not mention there what kind of a wireless adapter you have.

Post there output of the command I gave you before.

---

### Post by denis27 on 2014-12-02
Right :) done!

---

### Post by frmdstryr on 2014-12-13
> **guillaume-desclaux said:**
> To solve the touchpad issue, you should give a try to this custom kernel with Focaltech driver enabled ! A big Thanks for all the work done by these guys on this thread : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1372609](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1372609)  Keep up the good work !

Kernel with FocalTech support : [https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0](https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0)

Touchpad works great with this! Thanks!

---

### Post by pierre.fr34 on 2014-12-14
Hi everyone,

First thanks a lot for the work done. Trackpad and lightness control fully functionnal. I just got an error when installing the custom kernel from Pilot6 (I am on 14.04): the nvidia module was not built. I had to reinstall nvidia-331-updates after and it was then built without error.

Maybe it is just cosmetic, but the power/battery indicator does not detect when power supply is connected. It is always in battery mode. Could this have some influence on charging/preserving battery ? Any clue on how to fix it ?

Cheers,

Pierre

---

### Post by Pilot6 on 2014-12-14
Pierre,

I suggest making a bug report. Maybe someone will fix power indicator. I have another laptop model and here it works OK.

---

### Post by frmdstryr on 2014-12-14
> **denis27 said:**
> Pilot, since I've installed the 3.16 kernel, my wifi connection is going down very often (which wasn't the case on the official 3.13). Can we do something?

Also have this issue...  any ideas on how I might help solve it?

---

### Post by Pilot6 on 2014-12-14
What kind of wifi adapter you have?
Give output of

lspci -knn | grep Net -A2

---

### Post by frmdstryr on 2014-12-14
```
02:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 6b)
	Subsystem: Intel Corporation Dual Band Wireless-AC 7260 [8086:c170]
	Kernel driver in use: iwlwifi
```

It looks like the firmware is old?
[http://wireless.kernel.org/en/users/Drivers/iwlwifi](http://wireless.kernel.org/en/users/Drivers/iwlwifi)

shows there's a version 10, but /lib/firmware is only showing up to 9.  EDIT: Thats for kernel 3.17+...

```
$ ls /lib/firmware | grep 7260
iwlwifi-7260-7.ucode
iwlwifi-7260-8.ucode
iwlwifi-7260-9.ucode
```

---

### Post by Pilot6 on 2014-12-14
There will be some fixes for iwlwifi in next update of 3.16 kernel backported. So just wait a bit.

---

### Post by Pilot6 on 2014-12-16
Please test 3.16.0-29.39 build. There are upstream fixes for iwlwifi.
Both builds are at the same place.

[https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0](https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0)

---

### Post by frmdstryr on 2014-12-17
> **Pilot6 said:**
> Please test 3.16.0-29.39 build. There are upstream fixes for iwlwifi.
Both builds are at the same place.

[https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0](https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0)

This seems to have fixed the connectivity problems! Wifi hasn't dropped since installing this kernel, thanks!

---

### Post by frmdstryr on 2014-12-21
> **frmdstryr said:**
> This seems to have fixed the connectivity problems! Wifi hasn't dropped since installing this kernel, thanks!

Edit... this is still dropping connections, but only during high bandwidth operations (google hangouts w/video, large downloads, etc..), hopefully the 3.17 kernel will fix this... but I can at least stream music now :)

Edit 2. I can stream a video by disabling power management:

```
sudo iwconfig wlan0 power off
```

---

### Post by sundown on 2015-01-22
Hello, it's been awhile I've used linux on a dedicated system.

Don't know if I can complain about a wifi issue yet, given I'm on the 3.16.0-29.39 kernel.
And I'm not that much frustrated with the touchpad not providing full functionality, I can wait till 15.04 (or when the driver gets in the kernel in some form) ;)
Fixed the keyboard issues.

However, it's annoying that when I suspend the system and when I unsuspend it, the various opened windows i've previously had (browser, terminal) are not responsive and they can't be moved or clicked on, and also clicking on other Launcher applications gives no results.

I'm on the intel video version of ux303, so no nvidia.

Is this a known unity problem, I am not aware of or it's not unity at all?

---

### Post by Daëavelwyn on 2015-01-24
Hi here,

Ok, so first of all, really thanks to pilot6, your kernel is making touchpad working really well. So I just want to mention that neither networkmanager nor wicd succeeded in reconnecting to wireless network, although the first connection works well....Strange behaviour, but i've written scripts that I can use to connect easily with wpa_supplicant, and based on this post : [http://www.blackmoreops.com/2014/09/18/connect-to-wifi-network-from-command-line-in-linux/]("http://www.blackmoreops.com/2014/09/18/connect-to-wifi-network-from-command-line-in-linux/")

@pilot6, So, as i'm a musician, I'd lke to use my laptop for music with realtime processing, and, I'd like to know if you could provide the same kernel image with low-latency or real-time enabled (I usually used the ubnutustudio low-latency kernel provided by kxstudio).  If you couldn't (and I can understand such a request is hard to satisfy :) ). Could you indicate me how to make my own kernel low-latency (or real-time) with the changes you made to 3.16.0-29.39 which i'm actually using ?

regards,

---

### Post by Pilot6 on 2015-01-24
Daëavelwyn,

I can build a lowlatency image, but if I upload it with other images, it will confuse people.
You can make the image yourself. It is not hard.
Do you know how to use terminal, change directories there, etc?

---

### Post by Daëavelwyn on 2015-01-24
@pilot6 : Yes I know :)
The fact is I just can't find a clear how to about building a low-latency kernel (which patch? How to patch ? etc....) Perhaprs you could name the low-latency image (deb file) with low-latency in the file name to avoid confusion ?

---

### Post by Pilot6 on 2015-01-24
You do not need to patch anything. Here is the guide.

1. Get my source.

git clone [https://github.com/hanipouspilot/ubuntu-fixes.git/tree/pilot6](https://github.com/hanipouspilot/ubuntu-fixes.git/tree/pilot6)

You will get 3.16.0-30.40 already patched.

2. Then do some preparations.

cd ubuntu-fixes
fakeroot debian/rules clean

3. Copy my changelog form Dropbox -> next -> 3.16.0.30-40 to ~/ubuntu-fixes/debian/changelog

4. Then build

fakeroot debian/rules DEB_BUILD_OPTIONS=parallel=5  binary-headers binary-lowlatency

Where 5 is number of your cpu's or threads +1.

5. When you are asked if you want to build Focaltech module, just press Enter.

It will take some time.

You need to have some development packages installed. You can find which in any debian or ubuntu kernel build guide.

You will get deb files in directory where you cloned to.

---

### Post by Daëavelwyn on 2015-01-24
ok, i gonna try this, but The link you post for github repos is dead, Could please provide a valid link ? I've found your repos, but I guess it's not needed to clone all the repos :)

---

### Post by Pilot6 on 2015-01-24
The clone command was really wrong. Sry for that. Just clone pilot6 branch

git clone [https://github.com/hanipouspilot/ubuntu-fixes.git](https://github.com/hanipouspilot/ubuntu-fixes.git) --branch pilot6 --single-branch

---

### Post by Daëavelwyn on 2015-01-24
Ok thks, I give a try and let you know. Than ks for your help :)

---

### Post by Daëavelwyn on 2015-01-24
Arf :-(, I think I spoke to quickly about wifi, I can't make git clone finished the copy, but even with "sudo iwconfig wlan0 power off" entering, connection disconnect unexpectively :-/.

here is the wpa_supplicant output :
"wlan0: CTRL-EVENT-DISCONNECTED bssid=xx:xx:xx:xx:xx:xx reason=3"

:-/ I will try later with a faster connection.

---

### Post by Pilot6 on 2015-01-24
What wifi module do you have?

---

### Post by Daëavelwyn on 2015-01-24
lsmod :

iwlmvm                217686  0 
mac80211              652718  1 iwlmvm
iwlwifi               179412  1 iwlmvm
cfg80211              494330  3 iwlwifi,mac80211,iwlmvm


here is my firmware

root@Zenbook-MC ->ls /lib/firmware | grep 7260
iwlwifi-7260-7.ucode
iwlwifi-7260-8.ucode
iwlwifi-7260-9.ucode

---

### Post by Daëavelwyn on 2015-01-24
Ok, I finaly download the source and follow your instructions, but got this error at step 4 :

```

Debug: binary-headers
dh_installchangelogs -plinux-headers-3.16.0-30
Use of uninitialized value $package in hash element at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 478.
Use of uninitialized value $package in concatenation (.) or string at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 415.
Use of uninitialized value $package in concatenation (.) or string at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 429.
Use of uninitialized value $package in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 430.
Use of uninitialized value $Debian::Debhelper::Dh_Lib::dh{"MAINPACKAGE"} in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 430.
Use of uninitialized value $package in hash element at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 495.
dh_installchangelogs: package linux-headers-3.16.0-30 is not in control info
Use of uninitialized value $Debian::Debhelper::Dh_Lib::dh{"MAINPACKAGE"} in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 430.
Use of uninitialized value $Debian::Debhelper::Dh_Lib::dh{"MAINPACKAGE"} in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 430.
dh_installdocs -plinux-headers-3.16.0-30
dh_installdocs: package linux-headers-3.16.0-30 is not in control info
Use of uninitialized value $Debian::Debhelper::Dh_Lib::dh{"MAINPACKAGE"} in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 430.
Use of uninitialized value $Debian::Debhelper::Dh_Lib::dh{"MAINPACKAGE"} in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 430.
Use of uninitialized value $Debian::Debhelper::Dh_Lib::dh{"MAINPACKAGE"} in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 430.
Use of uninitialized value $Debian::Debhelper::Dh_Lib::dh{"MAINPACKAGE"} in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 430.
Use of uninitialized value $Debian::Debhelper::Dh_Lib::dh{"MAINPACKAGE"} in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 430.
Use of uninitialized value $dh{"MAINPACKAGE"} in string eq at /usr/bin/dh_installdocs line 279.
dh_compress -plinux-headers-3.16.0-30
Use of uninitialized value $Debian::Debhelper::Dh_Lib::dh{"MAINPACKAGE"} in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 430.
dh_fixperms -plinux-headers-3.16.0-30
dh_installdeb -plinux-headers-3.16.0-30
dh_installdeb: package linux-headers-3.16.0-30 is not in control info
Use of uninitialized value $Debian::Debhelper::Dh_Lib::dh{"MAINPACKAGE"} in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 430.
Use of uninitialized value $Debian::Debhelper::Dh_Lib::dh{"MAINPACKAGE"} in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 430.
Use of uninitialized value $Debian::Debhelper::Dh_Lib::dh{"MAINPACKAGE"} in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 430.
Use of uninitialized value $Debian::Debhelper::Dh_Lib::dh{"MAINPACKAGE"} in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 430.
Use of uninitialized value $Debian::Debhelper::Dh_Lib::dh{"MAINPACKAGE"} in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 430.
Use of uninitialized value $Debian::Debhelper::Dh_Lib::dh{"MAINPACKAGE"} in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 430.
Use of uninitialized value $Debian::Debhelper::Dh_Lib::dh{"MAINPACKAGE"} in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 430.
Use of uninitialized value $Debian::Debhelper::Dh_Lib::dh{"MAINPACKAGE"} in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 430.
flock -w 60 /home/mathieu/kernel-custom/ubuntu-fixes/debian/.LOCK dh_gencontrol -plinux-headers-3.16.0-30
Use of uninitialized value $Debian::Debhelper::Dh_Lib::dh{"MAINPACKAGE"} in string eq at /usr/share/perl5/Debian/Debhelper/Dh_Lib.pm line 430.
dpkg-gencontrol: error: no package stanza found in control info
dh_gencontrol: dpkg-gencontrol -ldebian/changelog -Tdebian/linux-headers-3.16.0-30.substvars -Pdebian/linux-headers-3.16.0-30 returned exit code 255
make: *** [binary-headers] Erreur 255 
```

[EDIT] Ok, i made a mistakes installing 3.16 headers, reinstalling and cleaning buid solve this. it's now compiling :)

---

### Post by Daëavelwyn on 2015-01-25
@pilot6 

Hey guy, really thanks for your help, it's working like a charm :). I still hav esome tests to do with realtime processing (lots of VSTi at the same time) but sounds raelly promising :)

Am I supposed to follow updates you (or someone else) could provide (git pull) often ? Or o you think I can use this kernel as long as I  want ?

---

### Post by Pilot6 on 2015-01-25
You can use this kernel or update mine, if you like. I will keep it intil the driver gets to official kernel.
I update every time the ubuntu kernel updates.

---

### Post by Daëavelwyn on 2015-01-25
@pilot6 : Ok, once again, really thanks for your help and your work :-)

---

### Post by miixxii on 2015-02-04
Hi,

First of all I would like to thanks to Pilot6 for the kernel. But I have one question and I hope you can help me. From time to time I need to use TTY but it's almost not possible to work in TTY with resolution 3200x1800. I've tried several things what I've found on forum like to update grub configuration but nothing is working. I always has 3K resolutuion in TTY. 

Did someone solved this ?

####

I've solved this with running dpkg-reconfigure console-setup and I've chosen Terminus -> 32x16

---

### Post by miixxii on 2015-02-04
> **sundown said:**
> Hello, it's been awhile I've used linux on a dedicated system.

Don't know if I can complain about a wifi issue yet, given I'm on the 3.16.0-29.39 kernel.
And I'm not that much frustrated with the touchpad not providing full functionality, I can wait till 15.04 (or when the driver gets in the kernel in some form) ;)
Fixed the keyboard issues.

However, it's annoying that when I suspend the system and when I unsuspend it, the various opened windows i've previously had (browser, terminal) are not responsive and they can't be moved or clicked on, and also clicking on other Launcher applications gives no results.

I'm on the intel video version of ux303, so no nvidia.

Is this a known unity problem, I am not aware of or it's not unity at all?

[COLOR=#000000]Hi,[/COLOR]

[COLOR=#000000]I'm facing same issue on intel video. To have your screen again working you need to switch to TTY and back (ctrl + alt + F1 and after ctrl +alt +F7)[/COLOR]

---

### Post by sundown on 2015-02-12
Hi guys,
I installed the daily kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/) . The touchpad driver is already there. I wanted to be able to turn the darn thing off.
On boot there will be a small warning message that iwlwifi-7260-10.ucode is missing and it reverts back to v9, but that's easily fixable by manually putting v10 in /lib/firmware/ after downloading it.

BUT
The function keys: brightness, volumes, keyboard lights, etc. are not working now :)
Even though **GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="** is written in **/etc/default/grub** and I have rebuilt grub and removed the previous kernels.

Any ideas what might fix this :)?
Thanks

---

### Post by pi32 on 2015-02-12
Hi guys,

FIrst of all thanks a lot for your work, it always a pleasure for me to deal with the ubuntu community when I am purchasing a new computer and facing issues :).

I tried to install the kernel headers given by Pilot6 but it didn't enable my trackpad. Since I am running Elementary OS Freya beta 2, I was wondering if it had anything to do with the kernel (which should be similar) or any other software EOS is running.I know this question has no straight answer I am just looking for a direction on where to dig to debug this ;)

Thanks!

---

### Post by Pilot6 on 2015-02-12
pi32,

Why did you install only headers? It won't fix anything.

---

### Post by Pilot6 on 2015-02-12
sundown,

You may fix this by installing normal kernel.

---

### Post by pi32 on 2015-02-12
Thanks for the quick answer! I might have given a wrong message, but I installed the 4 packages included in your Dropbox folder (using [COLOR=#3B3B3B][FONT=Georgia]sudo dpkg -i *.deb or even one by one with the sofware installer[/FONT][/COLOR]). 

I just though these are only headers but my linux knowledge is still limited when it comes to kernel.

---

### Post by Pilot6 on 2015-02-12
pi32,

Please give output of

uname -a

---

### Post by pi32 on 2015-02-12
Here it is:
```
Linux pi32-Laptop 3.13.0-45-generic #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by Pilot6 on 2015-02-12
This shows that you did not install my kernel image.

---

### Post by pi32 on 2015-02-12
Hmm... Well at least I have my answer :)

Let's sum up the steps to make sure I haven't missed anything:
1 - Go there [https://www.dropbox.com/sh/07642x3lziqgmz9/AAC6m_tMCBKQXDWT34udpkKHa/stable/3.16.0-30.40?dl=0](https://www.dropbox.com/sh/07642x3lziqgmz9/AAC6m_tMCBKQXDWT34udpkKHa/stable/3.16.0-30.40?dl=0)
2 - Download and unzip package
3 - execute the 4 .deb 
4 - reboot

That's why I did and even now if I open the .deb in the software center it appears as installed and only propose me to reinstall.
I'm going to give a shot again. If you have any suggestion, I'll take it!

Thanks a lot for your help in any case, I truly appreciate the support.

EDIT: Got it, I was booting on the wrong kernel. Sorry for loosing your time! And thanks again, it works brilliantly.

---

### Post by Pilot6 on 2015-02-12
There is nothing to unzip. Just put 4 debs to your home folder amd run

sudo dpkg -i linux*.deb

---

### Post by pi32 on 2015-02-12
That's what I was doing, but I was just booting on the wrong kernel ;)

---

### Post by phantom-s on 2015-02-15
Guys,

Thank you for the custom kernel! Touchpad and touch screen are working perfectly!

But I found  quite strange bug and according to the following trouble shooting guide that might be an kernel issue: [https://wiki.ubuntu.com/Hotkeys/Troubleshooting](https://wiki.ubuntu.com/Hotkeys/Troubleshooting)

So issue is following:
Sometimes after waking up after a sleep some shortcuts are not working. That's interesting because shortcuts like "Alt", "Super", "ctrl-alt-left" work as expected, but "Ctrl-Alt-T" or media buttons for Volume Up/Down stop working.
Any ideas?

Btw, I have one more issue, but not sure that it's directly related to our hardware...
Ubuntu configure in that way: if power is low laptop should hibernate. (Configured according to this instructions: [http://ubuntuhandbook.org/index.php/2014/04/enable-hibernate-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/04/enable-hibernate-ubuntu-14-04/))
But, when power is really low laptop continue working till force shutdown because of no power... At the same time power indicator is working perfectly a long as pm-hibernate.

---

### Post by phantom-s on 2015-02-16
I figured out that issue is related to uniti-settings-daemon crash ticket: [https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1328347](https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1328347)
I see it's not "common" issue for 14.04 so might be related to our hardware: UX303LN and new kernel. If I'm correct: there is something about touch device in a crash dump.

---

### Post by Mr._Anderson on 2015-02-24
> **guillaume-desclaux said:**
> To solve the brightness buttons problem, you have to add the option acpi_osi without value in your /etc/default/grub file like this :

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

and then : update-grub

Hi there!

After a few hours I finally managed to get almost everything to work except the keys for the brightness.
I'm running Ubuntu 14.10 with the kernel 3.17.0-focaltech-debug on a brandnew UX303LA.
I already tried different acpi_osi options (no value, Windows2012, Linux, etc) as well as a newer kernel (3.19., touchpad and brightness not working).
If I run acpi_listen nothing comes up for Fn+F5/F6. 
Any ideas what else I could try?
Thanks in advance.

---

### Post by miixxii on 2015-02-28
> **Mr._Anderson said:**
> Hi there!

After a few hours I finally managed to get almost everything to work except the keys for the brightness.
I'm running Ubuntu 14.10 with the kernel 3.17.0-focaltech-debug on a brandnew UX303LA.
I already tried different acpi_osi options (no value, Windows2012, Linux, etc) as well as a newer kernel (3.19., touchpad and brightness not working).
If I run acpi_listen nothing comes up for Fn+F5/F6. 
Any ideas what else I could try?
Thanks in advance.

Hello,

I have zenbook UX303LN also running ubuntu 14.10

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="   in /etc/default/grub working fine ( my brigness keyboard are working) 
Did you apply changes after you updated /etc/default/grub ? run update-grub

for touchpad use kernel from Pilot6

---

### Post by phantom-s on 2015-03-07
Guys,

Let me summarize all issues with ux303ln. 

1) No support of trackpad on default ubuntu kernel. To fix: install custom kernel from Pilot6 ([https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0](https://www.dropbox.com/sh/07642x3lziqgmz9/AACGWNO5_lNnX7x7tYMoH9gka?dl=0))
2) Brightness buttons doesn't work. To fix: Modify your[COLOR=#000000]* /etc/default/grub to add '*[/COLOR][COLOR=#000000]*acpi_osi=' into kernel parameters. For example: *[/COLOR][COLOR=#000000][I]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=". And then run update-grub
[/I][/COLOR]3) Very weak wifi. There is no good fix. Some better performance might be achived by disabling of power management by 'iwconfig wlan0 power off'. But even after this change download speed significantly drop if you will go more far from access point.
4) Battery. It's real issue. Even with enabled 'tlp', disabled NVIDIA card and tuned all possible settings in powertop: discharge is around 10-16 (13 in avg). Prediction of battery is worst as well.
5) Well known issue with "yellow screen". This issue is not strong in comparison with Win8 due to color profile installed automatically for UX303LN.

---

### Post by thananop.k on 2015-03-07
[SIZE=3][FONT=arial]even with a new kernel from pilot6, I still cannot use brightness button. This is an output from uname -r.

Linux Ton 3.16.0-32-generic #42 SMP Wed Mar 4 19:52:44 MSK 2015 x86_64 x86_64 x86_64 GNU/Linux

I already add acpi_osi= at the end of grub commandline and run "update-grub". This combination make brightness cannot be adjust anymore. But If I didn't add any grub commandline, the brightness can still adjust from System Settings > Brightness&Lock

For addition information,I'm using [COLOR=#141823]R4280H model (new ux303ln + gen 5 i7) and 206 bios
acpi_listen doesn't show anything when i'm pressing fn+f5/f6 and also fn+f2/f8 but other fn key works perfectly[/COLOR][/FONT][/SIZE]

---

### Post by azorin2 on 2015-03-09
Regarding the WiFi, have you tried installing the Windows version of the WiFi drivers using the Windows Wireless Drivers program (ndiswrapper)?

---

### Post by miixxii on 2015-03-10
> **thananop.k said:**
> [SIZE=3][FONT=arial]even with a new kernel from pilot6, I still cannot use brightness button. This is an output from uname -r.

Linux Ton 3.16.0-32-generic #42 SMP Wed Mar 4 19:52:44 MSK 2015 x86_64 x86_64 x86_64 GNU/Linux

I already add acpi_osi= at the end of grub commandline and run "update-grub". This combination make brightness cannot be adjust anymore. But If I didn't add any grub commandline, the brightness can still adjust from System Settings > Brightness&Lock

For addition information,I'm using [COLOR=#141823]R4280H model (new ux303ln + gen 5 i7) and 206 bios
acpi_listen doesn't show anything when i'm pressing fn+f5/f6 and also fn+f2/f8 but other fn key works perfectly[/COLOR][/FONT][/SIZE]

This is my /etc/default/grub file [ATTACH]260552[/ATTACH] I have same asus ux303ln and fir me it's working without problems

---

### Post by thananop.k on 2015-03-12
I already try acpi_osi= but it still not work! I have to remind you that i'm using a new model of ux303ln (UX303LN**B**) + 206 BIOS [**new Broadwell not Haswell Mode**l] may be there's something change in the BIOS. 

This is a result from dmidecode
[http://pastebin.com/z2nVGNC8](http://pastebin.com/z2nVGNC8)

I try many combination of acpi_osi and result show below

**acpi_osi= Linux video.use_native_backlight=1 **
- in /sys/class/backlight there will be acpi_video0 / intel_backlight But when I adjust backlight in System settings, brightness in acpi_video0 will change but not for intel_backlight. So, I can't adjust the brightness.
- acpi_listen can detect every fn combination except fn+f5 & fn+f6

[B]acpi_osi= 
[/B]- in /sys/class/backlight there will be acpi_video0 / intel_backlight But when I adjust backlight in System settings, brightness in acpi_video0 will change but not for intel_backlight. So, I can't adjust the brightness
- acpi_listen can detect every fn combination except  fn+f5 & fn+f6

**acpi_osi= ****video.use_native_backlight=1 **same as [B]acpi_osi= 
[/B]
[B]acpi_osi='!Windows 2012'  video.use_native_backlight=1 
[/B]- in /sys/class/backlight there will be only intel_backlight (brightness can be adjust properly from system-settings)- acpi_listen can detect every fn combination except fn+f2 / fn+f5 / fn+f6 / fn+f8

---

### Post by emq2 on 2015-03-12
> **thananop.k said:**
> I already try acpi_osi= but it still not work! I have to remind you that i'm using a new model of ux303ln (UX303LN**B**) + 206 BIOS [**new Broadwell not Haswell Mode**l] may be there's something change in the BIOS.

Bought same machine like two days ago, same issues like yours (tried bios 204 & 206) - can't get that back-light keys to work :{. I think I tried every combination for acpi in grub settings, so not sure if this is the solution...

Also - super thanks for patched kernel, resolved touchpad issues (fun fact: can't get touch pad gestured to work under win 8.1 :P)

---

### Post by Pilot6 on 2015-03-12
> **thananop.k said:**
> I already try acpi_osi= but it still not work! I have to remind you that i'm using a new model of ux303ln (UX303LN**B**) + 206 BIOS [**new Broadwell not Haswell Mode**l] may be there's something change in the BIOS. 

This is a result from dmidecode
[http://pastebin.com/z2nVGNC8](http://pastebin.com/z2nVGNC8)

I try many combination of acpi_osi and result show below

**acpi_osi= Linux video.use_native_backlight=1 **
- in /sys/class/backlight there will be acpi_video0 / intel_backlight But when I adjust backlight in System settings, brightness in acpi_video0 will change but not for intel_backlight. So, I can't adjust the brightness.
- acpi_listen can detect every fn combination except fn+f5 & fn+f6

[B]acpi_osi= 
[/B]- in /sys/class/backlight there will be acpi_video0 / intel_backlight But when I adjust backlight in System settings, brightness in acpi_video0 will change but not for intel_backlight. So, I can't adjust the brightness
- acpi_listen can detect every fn combination except  fn+f5 & fn+f6

**acpi_osi= ****video.use_native_backlight=1 **same as [B]acpi_osi= 
[/B]
[B]acpi_osi='!Windows 2012'  video.use_native_backlight=1 
[/B]- in /sys/class/backlight there will be only intel_backlight (brightness can be adjust properly from system-settings)- acpi_listen can detect every fn combination except fn+f2 / fn+f5 / fn+f6 / fn+f8

Solution is quite easy. Use only 'acpi_osi='
To adjust brightness using buttons just add a file /usr/share/X11/xorg.conf.d/20-intel.conf
containing

```
Section "Device"   Identifier    "Card0"
   Driver           "intel"
   Option          "Backlight"     "intel_backlight"
   BusID    "PCI:0:2:0"
EndSection
```

---

### Post by thananop.k on 2015-03-13
I already try Pilot6 solution. Now I can adjust brightness through system-setting but adjusting through fn+f5/f6 still not working.

---

### Post by Pilot6 on 2015-03-13
> **thananop.k said:**
> I already try Pilot6 solution. Now I can adjust brightness through system-setting but adjusting through fn+f5/f6 still not working.
Did you set "acpi_osi=" in /etc/default/grub?
Did you run sudo update-grub?

---

### Post by thananop.k on 2015-03-13
sry double post

---

### Post by thananop.k on 2015-03-13
> **Pilot6 said:**
> Did you set "acpi_osi=" in /etc/default/grub?
Did you run sudo update-grub?

[COLOR=#000000]yep i already set acpi_osi= / save then run sudo update-grub.[/COLOR]

---

### Post by Pilot6 on 2015-03-13
Please give output of

cat /etc/default/grub

---

### Post by thananop.k on 2015-03-13
> **Pilot6 said:**
> Please give output of

cat /etc/default/grub

Here it is, [http://pastebin.com/v1qNZXZ1](http://pastebin.com/v1qNZXZ1)

and uname -a output 
Linux Ton 3.16.0-33-generic #44 SMP Thu Mar 12 20:01:34 MSK 2015 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Pilot6 on 2015-03-13
It looks OK. I have no ideas why it may not work on your laptop.
Sometime Intel will fix this bug.

---

### Post by thananop.k on 2015-03-13
Anyone who has a problem with UX303**LNB [New Broadwell Model] **please join and discuss here

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1348890](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1348890)

---

### Post by azorin2 on 2015-03-26
> **phantom-s said:**
> [COLOR=#000000][/COLOR]3) Very weak wifi. There is no good fix. Some better performance might be achived by disabling of power management by 'iwconfig wlan0 power off'. But even after this change download speed significantly drop if you will go more far from access point.

Has anyone tried installing the Windows version of the WiFi drivers using the Windows Wireless Drivers program (ndiswrapper) to see if it fixes this issue?

---

### Post by wadelius on 2015-04-06
To get quick access to the brightness control from the indicator menu instead of the keys there is a nifty app called *indicator-brightness*.

I installed it by manally downloading the deb for 14.04 linked to from here: [http://ubuntuhandbook.org/index.php/2014/11/install-brightness-indicator-ubuntu-1410/](http://ubuntuhandbook.org/index.php/2014/11/install-brightness-indicator-ubuntu-1410/)

To fix the missing icon I created the folder [FONT=courier new]/usr/share/notify-osd/icons/gnome/scalable/status[/FONT], navigated to it with a terminal, and then created a symbolic link to the correct svg:
```
jowa@zenbook:/usr/share/notify-osd/icons/gnome/scalable/status$ sudo ln -s ../../../Humanity/scalable/status/notification-display-brightness-full.svg notification-display-brightness-full.svg
```

To start the app from the dash, type *Brightness Indicator*. It's possible to control the app with custom key bindings, but using the touchpad is enough for me.

I'm on 15.04 beta 2.

---

### Post by c51 on 2015-04-13
> **guillaume-desclaux said:**
> To solve the brightness buttons problem, you have to add the option acpi_osi without value in your /etc/default/grub file like this :

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

and then : update-grub
Just wondering: is this only a workaround until ASUS releases a updated BIOS?

Currently I'm going through my dmesg log and try to find/resolve issues.

One thing I stumbled upon the following lines:

```

sudo dmesg |grep  -e OSI -e "ACPI Error" -e "ACPI Warning"
[    0.000000] ACPI: _OSI method disabled
[    0.176477] ACPI: Added _OSI(Module Device)
[    0.176480] ACPI: Added _OSI(Processor Device)
[    0.176481] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.176483] ACPI: Added _OSI(Processor Aggregator Device)
[    0.234299] ACPI Error: [_OSI] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)
[    0.234304] ACPI Error: Method parse/execution failed [\_SB_.BTKL._STA] (Node ffff88032203ac08), AE_NOT_FOUND (20140424/psparse-536)
[    0.234320] ACPI Error: [_OSI] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)
[    0.234323] ACPI Error: Method parse/execution failed [\_SB_.BTKL._STA] (Node ffff88032203ac08), AE_NOT_FOUND (20140424/psparse-536)
[    0.257738] ACPI Error: [_OSI] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)
[    0.257742] ACPI Error: Method parse/execution failed [\_SB_.BTKL._STA] (Node ffff88032203ac08), AE_NOT_FOUND (20140424/psparse-536)
[    0.269781] ACPI Error: [_OSI] Namespace lookup failure, AE_NOT_FOUND (20140424/psargs-359)
[    0.269786] ACPI Error: Method parse/execution failed [\_SB_.BTKL._STA] (Node ffff88032203ac08), AE_NOT_FOUND (20140424/psparse-536)
[    0.960579] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140424/nsarguments-95)
[    0.960649] ACPI Warning: \_SB_.PCI0.RP05.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20140424/nsarguments-95)

```

I read that this might be related to bluetooth, which indeed reminded me of having an issue with a bluetooth device. It's Apple's Magic Trackpad I want to use together with my UX303 since my iMac does not work anymore.

The trackpad works for a certain time and then hangs. After some time it starts to work again and so on....
Might this be related?
[Here]("https://bugzilla.kernel.org/show_bug.cgi?id=62151") I read (comment #2) that this is related to the "acpi_osi=" kernel option.

---

### Post by Pilot6 on 2015-04-13
c51,

It has nothing to do with bios. It has to be fixed in kernel. This is a task for Intel.

---

### Post by c51 on 2015-04-13
> **Pilot6 said:**
> c51,

It has nothing to do with bios. It has to be fixed in kernel. This is a task for Intel.
Cool, maybe this already is fixed... I will try to boot with a more recent live image later this week and see if these ACPI errors still persist.

[B][Edit]
Is this something to be reported to Intel?
[/Edit]
[/B]
So last thing I am adressing now is a bunch of "*BAD*grain_size" lines.

Already tried to append some individual mtrr params to the boot options, without having "success".

I replaced the non-soldered 4GB module with an 8GB module having a total of 12GB RAM. Sadly I did not have a chance to have a look at the dmesg output of the original configuration. It's only 2-4 MB I'm losing, so nothing really to be concerned about, unless one wants to have a geeky perfect system (which applies to me :-)).

I guess I will start another thread for that specific issue and leave a link to it here. And thank you, **Pilot6**, for your quick responses.

Regards,
c51

---

### Post by jos3k4 on 2015-04-15
I bought an UX303 Asus...this laptop is amazing but like everybody say here it have some problems with the hardware and Linux...So I've tried the solution of Pilot6 (That worked for everyone) but for some reason when I install the **deb **packages the entry in the Grub for the pilot6 kernel doesn't appear.

Searching more about this I found another compiled kernel that have all those fixes and worked for me! (Touchpad,Brightness,lights of the keyboard) so I show here the output of my amazing kernel.

```

# Output of uname -a
Linux LJCUX303 3.19.0-rc4-focaltech-fix2 #1 SMP Wed Feb 18 23:58:56 CET 2015 x86_64 x86_64 x86_64 GNU/Linux

```

And here is my list of devices

```

&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; Atmel Atmel maXTouch Digitizer              id=10    [slave  pointer  (2)]
&#9116;   &#8627; FocalTechPS/2 FocalTech FocalTech Touchpad    id=13    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; USB2.0 UVC HD Webcam                        id=9    [slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                            id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]

```

If someone searching in Google try the pilot6 solution and doesn't work (Maybe there is some problem with the Elementary OS distro) you can use this solution that worked for me. So in order to make things clear.

[LIST=1]
[*]Download the kernel that [FONT=Roboto Slab]Mathias Gotschlag (thanks!) has modified and compiled - [/FONT][https://drive.google.com/file/d/0Bz7ZZcjnECHLR2EwTVdYd0VWdGc/view?pli=1](https://drive.google.com/file/d/0Bz7ZZcjnECHLR2EwTVdYd0VWdGc/view?pli=1)
[*]bunzip2 and tar -xf when you download the file
[*]you will have 3 **deb **files. So -> sudo dpkg -i *.deb
[*]If everything goes fine during the process, reboot your machine and select that kernel in GRUB
[*]Enjoy Linux in your Asus ux303
[/LIST]

---

### Post by Pilot6 on 2015-04-15
> **jos3k4 said:**
> I bought an UX303 Asus...this laptop is amazing but like everybody say here it have some problems with the hardware and Linux...So I've tried the solution of Pilot6 (That worked for everyone) but for some reason when I install the **deb **packages the entry in the Grub for the pilot6 kernel doesn't appear.

Searching more about this I found another compiled kernel that have all those fixes and worked for me! (Touchpad,Brightness,lights of the keyboard) so I show here the output of my amazing kernel.



You probably did not install it right. Mathias's kernel works too. But now I made an easier solution for trusty and vivid.
I made a ppa with focaltech driver in dkms format.
[https://launchpad.net/~hanipouspilot/+archive/ubuntu/focaltech-dkms](https://launchpad.net/~hanipouspilot/+archive/ubuntu/focaltech-dkms)
For vivid it will work out-of-the-box now.
For trusty before linux-generic-lts-vivid (3.19) is in main repos, this package must be installed.
It can be found in [COLOR=#333333][FONT=monospace]ppa:canonical-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]kernel-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]team/ppa

It pulls 3.19.0-12 kernel, which is not too good. I suggest after installing that package install latest ubuntu kernel from vivid repos.
Or just wait till kernel is updated in [/FONT][/COLOR][COLOR=#333333][FONT=monospace]canonical-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]kernel-[/FONT][/COLOR][COLOR=#333333][FONT=monospace]team/ppa. Or wait a couple of weeks till this package with 3.19 kernels are available in main Ubuntu repos.

Dkms driver is a much better solution, then just install some kernel image, or update kernel from my builds. The driver will autocompile against new kernels. Thus all security updates and fixes will be installed.

That is why I am dropping support of 3.16 kernels with Focaltech. If it makes too big trouble for someone, please, tell me.[/FONT][/COLOR]

---

### Post by jos3k4 on 2015-04-15
> [COLOR=#000000]You probably did not install it right. Mathias's kernel works too. But now I made an easier solution for trusty and vivid.[/COLOR]

I've done the same steps for install your kernel that I did for install the one that is working in my laptop...don't know where I can do something wrong. Anyway the last solution that you propose is better for everyone I think :)

Thanks pilot6 for your work here, Ubuntu have a great community

---

### Post by wadelius on 2015-04-24
Thanks a lot Pilot6! Works like a charm on 15.04.

---

### Post by robzi on 2015-04-27
Thank you for your work, has been a huge help! And now I hope you can help me more ;).

I am now running elementary os, and have succesfully managed to get the touchpad working. But with the 3.19 kernel, there seems to be some kind of hardware problem. On the 3.16 kernel the fans are quite and tlp reports an idle power usage of about 4W, while on 3.19 the fans run and the idle power is around 8W. Do you have any idea how to solve the problem? Could it be that the nvidia driver I'm using (331) doesn't work on 3.19?

---

### Post by Pilot6 on 2015-04-27
> **robzi said:**
> Thank you for your work, has been a huge help! And now I hope you can help me more ;).

I am now running elementary os, and have succesfully managed to get the touchpad working. But with the 3.19 kernel, there seems to be some kind of hardware problem. On the 3.16 kernel the fans are quite and tlp reports an idle power usage of about 4W, while on 3.19 the fans run and the idle power is around 8W. Do you have any idea how to solve the problem? Could it be that the nvidia driver I'm using (331) doesn't work on 3.19?

Maybe video driver did not build. Give output of

 lspci -k | egrep 'VGA|3D' -A2
uname -a

---

### Post by robzi on 2015-04-27
> **Pilot6 said:**
> Maybe video driver did not build. Give output of

 lspci -k | egrep 'VGA|3D' -A2
uname -a

Here is the output when using kernel 3.19.

lspci -k | egrep 'VGA|3D' -A2
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
    Subsystem: ASUSTeK Computer Inc. Device 167d
    Kernel driver in use: i915
--
03:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 840M] (rev a2)
    Subsystem: ASUSTeK Computer Inc. Device 167d

uname -a
Linux robert-UX303LN 3.19.0-12-generic #12~14.04.1-Ubuntu SMP Wed Apr 8 10:44:01 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by Pilot6 on 2015-04-27
3.12 kernel has issues. Update it.

---

### Post by robzi on 2015-04-27
What do you mean by kernel 3.12? For all I know, I'm using 3.19.

---

### Post by Pilot6 on 2015-04-27
3.19.0-12

---

### Post by robzi on 2015-04-27
I'm sorry, but what is the easiest way to do this? I got this kernel when installing the "linux-generic-lts-vivid" package.

---

### Post by Pilot6 on 2015-04-27
Oh, I see. It is too early to use it on trusty. I hope this it week it will be fixed.

I would do this way. Download these packages.

[http://mirrors.kernel.org/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.19.0.15.14_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.19.0.15.14_amd64.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-3.19.0-15_3.19.0-15.15_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-3.19.0-15_3.19.0-15.15_all.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-image-3.19.0-15-generic_3.19.0-15.15_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-image-3.19.0-15-generic_3.19.0-15.15_amd64.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-image-extra-3.19.0-15-generic_3.19.0-15.15_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-image-extra-3.19.0-15-generic_3.19.0-15.15_amd64.deb)

And install them all.

Latest 3.19 Ubuntu kernel will be installed. As soon as linux-generic-lts-vivid appears in main repos, just remove canonical-kernel-team ppa.

---

### Post by robzi on 2015-04-27
Thanks for the help so far!

I encounter more problems when I try to install those packages. Here is the message from the command line:

sudo dpkg -i linux-headers-*.deb linux-image-*.deb


(Reading database ... 191939 files and directories currently installed.)
Preparing to unpack linux-headers-3.19.0-15_3.19.0-15.15_all.deb ...
Unpacking linux-headers-3.19.0-15 (3.19.0-15.15) over (3.19.0-15.15) ...
Selecting previously unselected package linux-headers-generic.
Preparing to unpack linux-headers-generic_3.19.0.15.14_amd64.deb ...
Unpacking linux-headers-generic (3.19.0.15.14) ...
Preparing to unpack linux-image-3.19.0-15-generic_3.19.0-15.15_amd64.deb ...
Done.
Unpacking linux-image-3.19.0-15-generic (3.19.0-15.15) over (3.19.0-15.15) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-15-generic /boot/vmlinuz-3.19.0-15-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-15-generic /boot/vmlinuz-3.19.0-15-generic
Selecting previously unselected package linux-image-extra-3.19.0-15-generic.
Preparing to unpack linux-image-extra-3.19.0-15-generic_3.19.0-15.15_amd64.deb ...
Unpacking linux-image-extra-3.19.0-15-generic (3.19.0-15.15) ...
Setting up linux-headers-3.19.0-15 (3.19.0-15.15) ...
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.19.0-15-generic; however:
  Package linux-headers-3.19.0-15-generic is not installed.


dpkg: error processing package linux-headers-generic (--install):
 dependency problems - leaving unconfigured
Setting up linux-image-3.19.0-15-generic (3.19.0-15.15) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Failed to symbolic-link boot/initrd.img-3.19.0-15-generic to initrd.img:File exists at /var/lib/dpkg/info/linux-image-3.19.0-15-generic.postinst line 629.
dpkg: error processing package linux-image-3.19.0-15-generic (--install):
 subprocess installed post-installation script returned error exit status 17
dpkg: dependency problems prevent configuration of linux-image-extra-3.19.0-15-generic:
 linux-image-extra-3.19.0-15-generic depends on linux-image-3.19.0-15-generic; however:
  Package linux-image-3.19.0-15-generic is not configured yet.


dpkg: error processing package linux-image-extra-3.19.0-15-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-generic
 linux-image-3.19.0-15-generic
 linux-image-extra-3.19.0-15-generic

---

### Post by robzi on 2015-04-27
And if I try to install [COLOR=#000000]linux-headers-3.19.0-15-generic [/COLOR]first I get this:

sudo dpkg -i linux-headers-generic_3.19.0.15.14_amd64.deb 
(Reading database ... 196175 files and directories currently installed.)
Preparing to unpack linux-headers-generic_3.19.0.15.14_amd64.deb ...
Unpacking linux-headers-generic (3.19.0.15.14) over (3.19.0.15.14) ...
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-3.19.0-15-generic; however:
  Package linux-headers-3.19.0-15-generic is not installed.


dpkg: error processing package linux-headers-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-generic

---

### Post by Pilot6 on 2015-04-27
I gave you a wrong package. Install this

[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-3.19.0-15-generic_3.19.0-15.15_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-3.19.0-15-generic_3.19.0-15.15_amd64.deb)

---

### Post by robzi on 2015-04-27
Is there a specific order I should install them? Because I still get errors. I'm new to this, as you may notice ^^.

---

### Post by Pilot6 on 2015-04-27
Just install the last package I gave link to. All others should install themselves, if you did not remove them.
Ot just install them all by dpkg -i linux*.deb

---

### Post by robzi on 2015-04-27
So there is no problem in that I have tried installing them and haven't removed anything?

---

### Post by Pilot6 on 2015-04-27
It is good. I did not mean you should remove anything.

---

### Post by robzi on 2015-04-27
By removing I didn't mean removing the files downloaded, but something else.

However, there are still errors.

sudo dpkg -i linux*.deb
(Reading database ... 205308 files and directories currently installed.)
Preparing to unpack linux-headers-3.19.0-15_3.19.0-15.15_all.deb ...
Unpacking linux-headers-3.19.0-15 (3.19.0-15.15) over (3.19.0-15.15) ...
Preparing to unpack linux-headers-3.19.0-15-generic_3.19.0-15.15_amd64.deb ...
Unpacking linux-headers-3.19.0-15-generic (3.19.0-15.15) over (3.19.0-15.15) ...
Preparing to unpack linux-headers-generic_3.19.0.15.14_amd64.deb ...
Unpacking linux-headers-generic (3.19.0.15.14) over (3.19.0.15.14) ...
Preparing to unpack linux-image-3.19.0-15-generic_3.19.0-15.15_amd64.deb ...
Done.
Unpacking linux-image-3.19.0-15-generic (3.19.0-15.15) over (3.19.0-15.15) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-15-generic /boot/vmlinuz-3.19.0-15-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-15-generic /boot/vmlinuz-3.19.0-15-generic
Preparing to unpack linux-image-extra-3.19.0-15-generic_3.19.0-15.15_amd64.deb ...
Unpacking linux-image-extra-3.19.0-15-generic (3.19.0-15.15) over (3.19.0-15.15) ...
Setting up linux-headers-3.19.0-15 (3.19.0-15.15) ...
Setting up linux-headers-3.19.0-15-generic (3.19.0-15.15) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.19.0-15-generic /boot/vmlinuz-3.19.0-15-generic
ERROR (dkms apport): kernel package linux-headers-3.19.0-15-generic is not supported
ERROR (dkms apport): kernel package linux-headers-3.19.0-15-generic is not supported
Error! Bad return status for module build on kernel: 3.19.0-15-generic (x86_64)
Consult /var/lib/dkms/nvidia-331-uvm/331.113/build/make.log for more information.
Error! Bad return status for module build on kernel: 3.19.0-15-generic (x86_64)
Consult /var/lib/dkms/nvidia-331/331.113/build/make.log for more information.
Setting up linux-headers-generic (3.19.0.15.14) ...
Setting up linux-image-3.19.0-15-generic (3.19.0-15.15) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Failed to symbolic-link boot/initrd.img-3.19.0-15-generic to initrd.img:File exists at /var/lib/dpkg/info/linux-image-3.19.0-15-generic.postinst line 629.
dpkg: error processing package linux-image-3.19.0-15-generic (--install):
 subprocess installed post-installation script returned error exit status 17
dpkg: dependency problems prevent configuration of linux-image-extra-3.19.0-15-generic:
 linux-image-extra-3.19.0-15-generic depends on linux-image-3.19.0-15-generic; however:
  Package linux-image-3.19.0-15-generic is not configured yet.


dpkg: error processing package linux-image-extra-3.19.0-15-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.19.0-15-generic
 linux-image-extra-3.19.0-15-generic

---

### Post by Pilot6 on 2015-04-27
sudo apt-get install -f

---

### Post by robzi on 2015-04-27
And here is the answer:

sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.19.0-15-generic (3.19.0-15.15) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Failed to symbolic-link boot/initrd.img-3.19.0-15-generic to initrd.img:File exists at /var/lib/dpkg/info/linux-image-3.19.0-15-generic.postinst line 629.
dpkg: error processing package linux-image-3.19.0-15-generic (--configure):
 subprocess installed post-installation script returned error exit status 17
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Pilot6 on 2015-04-27
sudo dpkg -r [COLOR=#000000] linux-image-3.19.0-15-generic [/COLOR]

---

### Post by robzi on 2015-04-27
Ok, so now were back at square one I guess? 

sudo dpkg -r linux-image-3.19.0-15-generic
(Reading database ... 205307 files and directories currently installed.)
Removing linux-image-3.19.0-15-generic (3.19.0-15.15) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-15-generic /boot/vmlinuz-3.19.0-15-generic
dkms: removing: bbswitch 0.7 (3.19.0-15-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  bbswitch
Version: 0.7
Kernel:  3.19.0-15-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


bbswitch.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-15-generic/extra/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.
dkms: removing: bcmwl 6.30.223.248+bdcom (3.19.0-15-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.248+bdcom
Kernel:  3.19.0-15-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-15-generic/extra/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


depmod....


DKMS: uninstall completed.
dkms: removing: focaltech 1.4~trusty1 (3.19.0-15-generic) (x86_64)


-------- Uninstall Beginning --------
Module:  focaltech
Version: 1.4~trusty1
Kernel:  3.19.0-15-generic (x86_64)
-------------------------------------


Status: Before uninstall, this module version was ACTIVE on this kernel.


psmouse.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-15-generic/extra/
 - Original module
   - Archived original module found in the DKMS tree
   - Moving it to: /lib/modules/3.19.0-15-generic/updates/
depmod....


: Unable to find an initial ram disk that I know how to handle.
Will not try to make an initrd.


Removing original_module from DKMS tree for kernel 3.19.0-15-generic (x86_64)


DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-15-generic /boot/vmlinuz-3.19.0-15-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-15-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-15-generic /boot/vmlinuz-3.19.0-15-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-12-generic
Found initrd image: /boot/initrd.img-3.19.0-12-generic
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
robert@robert-UX303LN:~/Downloads$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-12-generic
Found initrd image: /boot/initrd.img-3.19.0-12-generic
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done

---

### Post by Pilot6 on 2015-04-27
sudo dpkg -i [COLOR=#000000] linux-image-3.19.0-15-generic

[/COLOR]

---

### Post by robzi on 2015-04-27
sudo dpkg -i linux-image-3.19.0-15-generic_3.19.0-15.15_amd64.deb
Selecting previously unselected package linux-image-3.19.0-15-generic.
(Reading database ... 204478 files and directories currently installed.)
Preparing to unpack linux-image-3.19.0-15-generic_3.19.0-15.15_amd64.deb ...
Done.
Unpacking linux-image-3.19.0-15-generic (3.19.0-15.15) ...
Setting up linux-image-3.19.0-15-generic (3.19.0-15.15) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-15-generic /boot/vmlinuz-3.19.0-15-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-15-generic /boot/vmlinuz-3.19.0-15-generic
ERROR (dkms apport): kernel package linux-headers-3.19.0-15-generic is not supported
ERROR (dkms apport): kernel package linux-headers-3.19.0-15-generic is not supported
Error! Bad return status for module build on kernel: 3.19.0-15-generic (x86_64)
Consult /var/lib/dkms/nvidia-331/331.113/build/make.log for more information.
Error! Bad return status for module build on kernel: 3.19.0-15-generic (x86_64)
Consult /var/lib/dkms/nvidia-331-uvm/331.113/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-15-generic /boot/vmlinuz-3.19.0-15-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-15-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-15-generic /boot/vmlinuz-3.19.0-15-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-15-generic /boot/vmlinuz-3.19.0-15-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-15-generic /boot/vmlinuz-3.19.0-15-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-15-generic
Found initrd image: /boot/initrd.img-3.19.0-15-generic
Found linux image: /boot/vmlinuz-3.19.0-12-generic
Found initrd image: /boot/initrd.img-3.19.0-12-generic
Found linux image: /boot/vmlinuz-3.16.0-34-generic
Found initrd image: /boot/initrd.img-3.16.0-34-generic
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done

---

### Post by Pilot6 on 2015-04-27
Looks good. Reboot.

But you may need to reinstall nvidia driver. Or maybe it is OK. That error message is a known bug.

---

### Post by robzi on 2015-04-27
Edit: Double

---

### Post by robzi on 2015-04-27
Thank you for helping with the installing of the kernel! More problems ahead though...I tried reinstalling the driver, but it doesn't behave too well. In the nvidia-prime application I can't change back to "performance mode"  (just met with a stop sign and it reverts to the intel driver) and power usage is still as high. So the driver 331 doesn't seem to go well with the kernel. Do you have any suggestions? I have tried with the latest drivers as well before, but with those I just got a black screen.

---

### Post by Pilot6 on 2015-04-27
```
sudo add-apt-repository &#8203;ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-346
sudo add-apt-repository -r ppa:xorg-edgers/ppa
```

---

### Post by robzi on 2015-04-27
Seems like we're coming to an end! The driver worked very well, apart from one thing. I don't seem to be able to initiate the power saving mode. I can enable it, but then have to re-log. When I do it is disabled. Do I have to install some special driver for the processor as well?

Edit: I do remember now that I didn't install any graphics driver, but used the one that comes with the distro. Searching for the relevant graphics installer, I found out that the support for 14.04 has been discontinued, and Intel no longer provides downloads for the earlier installers. Have tried to find another place to download from, but since this is a relatively new problem I couldn't find any. Maybe you have some special repository up your sleeve, as you did with the nvidia driver? ;)

---

### Post by robzi on 2015-04-27
And apart from the computer freezing. But I only need the driver to be able to disable the graphics card. Only uses it while gaming under Windows.

---

### Post by andrzej6 on 2015-04-27
Hello, I have this laptop with bradwell processor. I am using elementary OS, in order to make touchpad work i updated kernel to 4.0. Everything except Wifi works fine, system is not detecting any wifi card. I must mention that I am Linux beginner, could you help me resolve this issue?

---

### Post by robzi on 2015-04-27
I'm a bit of a beginner myself, but I think you should not use kernel 4 but the one I am trying to get to work, i.e. 3.19.0-15. You can try to follow the conversation I have had with pilot6.

EDIT: The only thing that is not working for me now is the power saving mode. No wifi issues.

---

### Post by Pilot6 on 2015-04-28
Yoy can use bumblebee for switching video.

---

### Post by robzi on 2015-04-28
[FONT=arial]Thank you very much. Worked perfectly!

For others who may run into the same problems.

To get graphics and touchpad working in Elementary OS on Asus Ux303LN Haswell:

1. Follow these instructions ([https://launchpad.net/~hanipouspilot/+archive/ubuntu/focaltech-dkms](https://launchpad.net/~hanipouspilot/+archive/ubuntu/focaltech-dkms)) to get the touchpad working.

When installing [COLOR=#333333]linux-generic-[/COLOR][COLOR=#333333]lts-vivid package [/COLOR]you get an outdated kernel by the name 3.19.0-12, we want to install kernel 3.19.0-15.

2. You need to download the following packages to the same folder.

[http://mirrors.kernel.org/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.19.0.15.14_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.19.0.15.14_amd64.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-3.19.0-15_3.19.0-15.15_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-3.19.0-15_3.19.0-15.15_all.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-image-3.19.0-15-generic_3.19.0-15.15_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-image-3.19.0-15-generic_3.19.0-15.15_amd64.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-image-extra-3.19.0-15-generic_3.19.0-15.15_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-image-extra-3.19.0-15-generic_3.19.0-15.15_amd64.deb)
[http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-3.19.0-15-generic_3.19.0-15.15_amd64.deb](http://mirrors.kernel.org/ubuntu/pool/main/l/linux/linux-headers-3.19.0-15-generic_3.19.0-15.15_amd64.deb)

3. Now, in the terminal, run:
```
sudo dpkg -i linux*.deb
```

4. Reboot.

5. Now you should be using the right kernel. If 
```
uname -r
```
 returns 
```
3.19.0-15-generic
```
you're OK.

6. To install a good driver for your graphics card (I am using 840M) do this:
```
sudo add-apt-repository &#8203;ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-346
sudo add-apt-repository -r ppa:xorg-edgers/ppa
```

7. Now, if you have problems in "nvidia x server settings" to change to the power saving profile, you need to install bumblebee. If not you're done here.

8. Installing bumblebee, I followed these instructions:

[COLOR=#111111]To install bumblebee in Ubuntu 14.04, run these commands in terminal
[/COLOR]```
sudo apt-get install bumblebee bumblebee-nvidia primus
```[COLOR=#111111]
[/COLOR][COLOR=#111111]
If you want a gui for Bumblebee (it is not needed), do the following:
[/COLOR][COLOR=#111111]
Install Python App Indicator:[/COLOR]
```
sudo apt-get install python-appindicator
```
[COLOR=#111111]
Install Git:[/COLOR]
```
sudo apt-get install git
```
[COLOR=#111111]
Make a directory for git:[/COLOR]
```
mkdir git && cd git
```
[COLOR=#111111]
Check out the repository:[/COLOR]
```
git clone [https://github.com/Bumblebee-Project/bumblebee-ui.git](https://github.com/Bumblebee-Project/bumblebee-ui.git)
cd bumblebee-ui
sudo ./INSTALL
```
[COLOR=#111111]
Open your startup applications by typing in the terminal:
```
gnome-session-properties
```

Add bumblebee indicator to start-up by writing *bumblebee-indicator* in the Command field. 

Rebooting should welcome you with a question mark icon in the top right. Clicking that icon it should say "Bumblebee: OFF". That means that you are now using your intel graphics card.



The above instructions worked for me, but there could be some deviations for your specific case.[/COLOR]

[/FONT]

---

### Post by robzi on 2015-04-28
Pilot6, if you could look through my post for errors I would be thankful!

---

### Post by Pilot6 on 2015-04-28
This is not correct. You need to install ALL packages not just  [COLOR=#000000][FONT=Ubuntu Mono]linux-image-3.19.0-15-generic_3.19.0-15.15_amd64.deb

So download them to home folder and run

sudo dpkg -i linux*.deb

Hopefully this week it won't be necessary. Linux-generic-lts-vivid will install automatically after maintainers add it to the main repos.[/FONT][/COLOR]

---

### Post by Pilot6 on 2015-04-28
And also there is no need to install bumblebee form source. There is a ppa for that.

---

### Post by robzi on 2015-04-28
Doesn't it get updated when installing it from source, or why would it matter?

---

### Post by andrzej6 on 2015-04-28
I installed 4.0 becouse i had problems with display([http://imgur.com/wFjDRAU](http://imgur.com/wFjDRAU)). On another forum i found info that instaling kernel 4.0 resolve this issue and it did. Why i should not install kernel 4 i read that it is stable?

---

### Post by Pilot6 on 2015-04-28
robzi,

1. It does not get updated
2. It won't work after kernel update.
3. It is generally a wrong way for Ubuntu.

---

### Post by Pilot6 on 2015-04-28
> **andrzej6 said:**
> I installed 4.0 becouse i had problems with display([http://imgur.com/wFjDRAU](http://imgur.com/wFjDRAU)). On another forum i found info that instaling kernel 4.0 resolve this issue and it did. Why i should not install kernel 4 i read that it is stable?

Kernel 4.0 is not supported by Ubuntu. You will have issues with it. But it is your choice to install it.

---

### Post by robzi on 2015-04-28
Then I learned something new. I thought everything you found from apt-get install needed to be in a ppa.

Edit: Ah, sorry. I guess you meant bumblebee-ui?

---

### Post by Pilot6 on 2015-04-28
You did not install bumblebee by apt-get. You downloaded source and compiled it.

---

### Post by robzi on 2015-04-28
After some research I found that bumblebee-ui doesn't seem to have a ppa.

---

### Post by Pilot6 on 2015-04-28
Gui is not that important. But you still can build a deb file from that source. Bumblebee itself has a kernel module.

---

### Post by robzi on 2015-04-28
I agree that it is not that important, but I installed the main bumblebee package from a ppa. It wouldn't matter that much if the gui stopped working.

---

### Post by robzi on 2015-04-28
Changed the post so that the ui is more of a "suggestion".

---

### Post by andrzej6 on 2015-04-28
I followed robzi's instructions and I installed kernel 3.9.0-15, but it did not fix my issue with graphic card(disappearing letters, partial windows/icons rendering, graphic artifact), more then that Wifi in not working on this kernel. I made some experiments and I installed drivers for geforce 840m. When i installed them system by default was using this dedicated graphic, and ther was no display issues. But i want to save some battery life so i turned it off in nvidia settings panel, after i did that display problems where back. So i asume ther is a problem with build in intel graphic card, is there a way to update drivers for this card? Or maybe you could help me resolve problems with Wifi on kernel 4.0? As a reminder i have asus ux303ln with broadwell processor.

---

### Post by thananop.k on 2015-04-29
Try to update to ubuntu 15.04 & add xorg-edger ppa. This version fix many problems (graphic artifact and slow wifi speed).

---

### Post by Klepsz on 2015-04-29
Hi!

I've Asus ux303ln with new brodwell processor i7-5500U. I'm using Ubuntu 15.04 with 3.19.0-15-generic kernel.
Everything works fine except touchpad. 

I've installed drivers from[FONT=courier new] ppa:hanipouspilot/focaltech-dkms[/FONT].
After reboot I typed [FONT=courier new]synclient PalmDetect=1 PalmMinZ=0[/FONT] [FONT=arial]and I received following error: [/FONT][FONT=courier new]Couldn't find synaptics properties. No synaptics driver loaded?[FONT=arial]

Touchpad in my computer is utterly dead. It's not even recognized as a mouse.

I'd appreciate any help :)[/FONT][/FONT]

---

### Post by Pilot6 on 2015-04-29
Klepsz,

It is strange a bit. Let's check if you properly installed the driver. Sometimes people close terminal too early befor they get command prompt.
Repulding initrd takes some time. Give output of

dkms status
dpkg -l | grep synaptics

And also you may try to reinstall the driver

sudo apt-get install --reinstall focaltech-dkms

---

### Post by Klepsz on 2015-04-29
Here's the output

[IMG]http://i.imgur.com/Troe4cU.png[/IMG]
 
I waited to the very end of installation process.

---

### Post by Pilot6 on 2015-04-29
This looks fine. For the future, you do not need to make pictures. Just copy text from the terminal and paste it to the forum.
Then give output of

xinput
dmesg | grep pnp

---

### Post by Klepsz on 2015-04-29
[FONT=courier new][SIZE=2][FONT=arial]ok. I received  something like this[/FONT][/SIZE]

[SIZE=1]wrobel@asus:~$ xinput[/SIZE][/FONT]
[SIZE=1][FONT=courier new]&#9121; Virtual core pointer                    	id=2	[master pointer  (3)][/FONT][/SIZE]
[SIZE=1][FONT=courier new]&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)][/FONT][/SIZE]
[SIZE=1][FONT=courier new]&#9116;   &#8627; Logitech M315/M235                      	id=10	[slave  pointer  (2)][/FONT][/SIZE]
[SIZE=1][FONT=courier new]&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)][/FONT][/SIZE]
[SIZE=1][FONT=courier new]    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)][/FONT][/SIZE]
[SIZE=1][FONT=courier new]    &#8627; Power Button                            	id=6	[slave  keyboard (3)][/FONT][/SIZE]
[SIZE=1][FONT=courier new]    &#8627; Video Bus                               	id=7	[slave  keyboard (3)][/FONT][/SIZE]
[SIZE=1][FONT=courier new]    &#8627; Video Bus                               	id=8	[slave  keyboard (3)][/FONT][/SIZE]
[SIZE=1][FONT=courier new]    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)][/FONT][/SIZE]
[SIZE=1][FONT=courier new]    &#8627; USB2.0 UVC HD Webcam                    	id=11	[slave  keyboard (3)][/FONT][/SIZE]
[SIZE=1][FONT=courier new]    &#8627; Asus WMI hotkeys                        	id=12	[slave  keyboard (3)][/FONT][/SIZE]
[SIZE=1][FONT=courier new]    &#8627; AT Translated Set 2 keyboard            	id=13	[slave  keyboard (3)][/FONT][/SIZE]
[SIZE=1][FONT=courier new]wrobel@asus:~$ dmesg | grep pnp[/FONT][/SIZE]
[SIZE=1][FONT=courier new][    0.198617] pnp: PnP ACPI init[/FONT][/SIZE]
[SIZE=1][FONT=courier new][    0.198823] pnp 00:01: Plug and Play ACPI device, IDs FLT0102 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)[/FONT][/SIZE]
[SIZE=1][FONT=courier new][    0.198856] pnp 00:02: Plug and Play ACPI device, IDs ATK3001 PNP030b (active)[/FONT][/SIZE]
[SIZE=1][FONT=courier new][    0.198972] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)[/FONT][/SIZE]
[SIZE=1][FONT=courier new][    0.199775] pnp: PnP ACPI: found 7 devices[/FONT][/SIZE]
[SIZE=1]
[/SIZE]

---

### Post by Pilot6 on 2015-04-29
You have a Focaltech touchpad for sure, but it is not detected.

Reboot and after that run command

dmesg > dmesg.log

And attach file dmesg.log from your home folder. Maybe you will need to zip or tar.gz it first.

And also add file 

/var/log/Xorg.0.log

---

### Post by Pilot6 on 2015-04-29
And BTW, try first to press Fn+F9 on the keyboard or whatever button is for your touchpad.  Maybe your touchpad is just turned off.

---

### Post by Klepsz on 2015-04-29
I tried to run Fn + F9 with no result.

Here are files you asked.[ATTACH]261655[/ATTACH][ATTACH]261656[/ATTACH]

---

### Post by Pilot6 on 2015-04-29
Your touchpad is not detected. I have no ideas why at the moment.
The only I can suggest now is to try to boot with upstart, not systemd. It can be done in grub menu.
I never tested the driver with systemd and do not know how can it affect things.

---

### Post by Klepsz on 2015-04-29
When I boot with upstart nothing change.
It's very strange situation. At the beginning when I've installed Ubuntu 14.04 touchpad was detected as a mouse. One day, with no reason it just stopped to work.
Maybe it's  just broken. Any ideas how can I check it? Maybe I should try some other OS :). Just in order to check touchpad of course :)
Pilot6, thanks for all quick responses.

---

### Post by Pilot6 on 2015-04-29
And another idea. Give output of

for i in /etc/modprobe.d/*; do ls $i; cat $i; done

---

### Post by Pilot6 on 2015-04-29
And if it just stopped working it may be because it is broken. Try to boot from LiveCD (flash drive with Ubuntu installer) and see if it is detected as a mouse at least.
But with this kernel it should be detected as Focaltech in mouse emulation mode. The previous command checks if psmouse module is blacklisted.
You might run some command and do it.

---

### Post by Klepsz on 2015-04-29
Output: [ATTACH]261660[/ATTACH]

When I run system in live mode from USB nothing's change.

---

### Post by Pilot6 on 2015-04-29
Looks OK. No ideas why psmouse does not start at all.

What does 

modprobe psmouse

say?

---

### Post by Klepsz on 2015-04-29
it gives nothing

---

### Post by Pilot6 on 2015-04-29
Sry, no more ideas. Try with LiveCD.
I have exactly same touchpad model.

---

### Post by Klepsz on 2015-04-29
You did what you can. Thanks.

---

### Post by Bob_McGee on 2015-04-30
I have the same laptop and I installed the xubuntu spin, but the trackpad didn't work (well, not to the
full extent it could, I could move the mouse and click left button). I then installed the 4.0 kernel deb
packages into place, did a reboot and everything works great.

I also use the powertop package to disable the nvidia GPU and get about 6 hrs on battery. Not awesome
but definitely better than the 2 I was getting after installation.

---

### Post by gmoutso on 2015-05-01
Good luck! I think yours is a focaltech clickpad. On my Asus TP500LN I have an elantech (etd0108) that needs psmouse patching to work. Try to search based on your clickpad model rather than your laptop model (in dmsg "pnp 00:06: Plug and Play ACPI device, IDs ETD0108 SYN0a00 SYN0002 PNP0f03 PNP0f13 PNP0f12 (active)" in mine)

---

### Post by Pilot6 on 2015-05-01
> **Bob_McGee said:**
> I have the same laptop and I installed the xubuntu spin, but the trackpad didn't work (well, not to the
full extent it could, I could move the mouse and click left button). I then installed the 4.0 kernel deb
packages into place, did a reboot and everything works great.

I also use the powertop package to disable the nvidia GPU and get about 6 hrs on battery. Not awesome
but definitely better than the 2 I was getting after installation.

The whole point of dkms driver is to backport the driver from 4.0, to Ubuntu kernel. It will get security updates.

---

### Post by Pilot6 on 2015-05-01
Good news is that lts-vivid kernel packages are currently building and will be available tonight for 14.04 users. Then package from ppa will work out of the box.

---

### Post by robzi on 2015-05-03
> **Bob_McGee said:**
> I have the same laptop and I installed the xubuntu spin, but the trackpad didn't work (well, not to the
full extent it could, I could move the mouse and click left button). I then installed the 4.0 kernel deb
packages into place, did a reboot and everything works great.

I also use the powertop package to disable the nvidia GPU and get about 6 hrs on battery. Not awesome
but definitely better than the 2 I was getting after installation.

It of course depends on usage, but I do not have a hard time reaching 8 hours on a charge using either elementary os or ubuntu. Have you tried tlp? Don't know how it compares to powertop, but it definetely works well for me.

---

### Post by andrzej6 on 2015-05-21
After I installed package provided by Pilot6 my touchpad works fine. Even gestures described here [https://wiki.ubuntu.com/Multitouch](https://wiki.ubuntu.com/Multitouch) are working correctly, Is there a way to change default behaviour of 3 fingers swipe gesture? I would like to switch between workspaces with this gesture.

---

### Post by HunterSBuntu on 2015-05-28
Hi everyone,

I'm about to go buy a Zenbook UX303LA.  I've read through all the Launchpad bug thread regarding the trackpad issues.  

I plan to install 15.04 on this machine.

Could someone give me a quick summary of the steps involved in getting trackpad support working on that version? 

Regarding the driver from Pilot 6:

1)Will I be able to get normal updates after applying it on 15.04 (3.19 kernel correct?)
2)Will it break during normal kernel updates (I'm guessing no as it is DKMS now?)
3)Planning to work with VirtualBox a good bit on this laptop.  Will anything with this driver impede that?  I've had quirkyness with Virtualbox before when installing Guest Additions it tells me I don't have matching kernel headers for the guest or something of that nature. 

I'm pretty comfortable with Linux at this point but haven't messed around with different kernels much yet.

Thank everyone, especially Pilot6 for your work on this.

---

### Post by Pilot6 on 2015-05-28
"yes", "yes", "no"

---

### Post by Pilot6 on 2015-05-28
You need to install the driver

```
sudo add-apt-repository ppa:hanipouspilot/focaltech-dkms
sudo apt-get update
sudo apt-get install focaltech-dkms
```

That's it.

---

### Post by HunterSBuntu on 2015-05-29
For the benefit of others who may find this thread I want to confirm that on a fresh 15.04 install on a UX303LA running the commands above works perfectly.

After a reboot two finger scroll works great.

Cheers Pilot6, really appreciate the effort you've put into this.

---

### Post by pi32 on 2015-06-02
Hi Pilot6,

After using the packages you proposed for a while I took the opportunity to use your ppa after a fresh install (ubuntu gnome 14.04)
However it seems that I can access alsamixer using this kernel (it works with the 3.16).
After typing sudo alsamixer I receive the error: cannot open mixer: No such file or directory

I guess the version is not compatible with your kernel. Any idea on which version of alsamixer I should install?

note: sound is working, it's just that the volume is pretty low on my external soundcard (presonus audiobox 44vsl) and with the other kernel I can play with alsamixer parameters to fix that.
Thanks!

---

### Post by Pilot6 on 2015-06-02
You installed kernel 3.19 with my package. Your sound problems are not related with the touchpad driver at all.
It is some problem with your hardware and the new kernel.

To install alsamixer you do

sudo apt-get install alsa-utils

---

### Post by pi32 on 2015-06-02
Ok I might have been confused.
But the thing is that when I installed the focaltec driver it installed the kernel 3.19 so I though it was linked.

alsa-utils is already installed but now that I understood the non-relation between your repo and the kernel I'm gonna do some research

---

### Post by thom-v on 2015-06-09
Just got my 303LA last night. Trackpad worked, but was a bit "wonky". Following these steps has made the trackpad stable and given me 2 finger scrolling. Thank you very much.

---

### Post by robrez on 2015-06-09
It's kind of difficult to scan this 20-page thread and get an idea of any current outstanding issues.

Does a list like that exist anywhere?

I'd really like to install 15.04 (or 14.04) on my ux303ln, but iff all of the following work:
- quadhd
- wireless ac
- trackpad

Anything obvious that I've left off. Is 15 or 14 the preferred install?

The best one-stop source of information I've encountered is here (used google translate to read it):
[http://www.christophe-meneses.fr/article/installer-ubuntu-sur-un-ordinateur-portable-asus-zenbook-ux303ln](http://www.christophe-meneses.fr/article/installer-ubuntu-sur-un-ordinateur-portable-asus-zenbook-ux303ln)

---

### Post by Pilot6 on 2015-06-09
I know for sure that wireless will work and touchpad with focaltech-dkms from ppa will.

14.04 LTS is preferred, especially if you are new to Ubuntu.

---

### Post by robrez on 2015-06-09
Pilot6, the man-myth-legend himself,

Thanks for the reply. I'm going to give it a whirl.

---

### Post by phantom-s on 2015-06-13
Guys,

After recent update of ubuntu touchscreen stoped work properly: single touch is working, but dragging and multi-touch don't.
Do you have ideas how to re-enable it?

P.S. touchpad works perfectly

---

### Post by Pilot6 on 2015-06-13
What is Ubuntu version, what is your touchpad, did you install any driver for touchpad?

---

### Post by phantom-s on 2015-06-15
> **Pilot6 said:**
> What is Ubuntu version, what is your touchpad, did you install any driver for touchpad?

Touchpad is good! There is a problem with touchscreen. It's working for single click, but dragging and multitouch doesn't work. Before regular update for Ubuntu 14.04 it was OK.

xinput:

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 FocalTech FocalTech Touchpad       	id=16	[slave  pointer  (2)]
&#9116;   &#8627; Atmel Atmel maXTouch Digitizer          	id=13	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=10	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Receiver                   	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB2.0 UVC HD Webcam                    	id=12	[slave  keyboard (3)]
    &#8627; Asus WMI hotkeys                        	id=14	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=15	[slave  keyboard (3)]

---

### Post by a-ranchalpedrosa-5 on 2015-06-18
Hi all,

I am having troubles installing ubuntu gnome 15.04 onto asus ux303la (intel i7, intel hd Graphics 5500). 
The screens flickers constantly, with not known solution at the moment. I tried adding nomodeset to kernel linux boot options and it works. However, if I use that workaround, then my screen does not turn on from sleep. That is, it works perfectly, then I suspend the computer and after that it resumes everything apart from the screen. It is important to remark that whith nomodeset my display is niot recognized as built-in display but as unknown display according to system settings > Display 

Checked new kernels (even 4.1) and they do not seem to fix this issue. I will appreciate any suggestion at this point (I am kinda desperate)

---

### Post by thom-v on 2015-06-25
So far this machine is working out great for me on Ubuntu 15.04. The main thing I've noticed is certain function keys not working. Namely Airplane Mode (F2), Brightness (F5 & F6), and Auto Brightness (A). I'm not sure if that last one is for the screen or keyboards.

I was having trouble searching through the thread for ideas on these and was wondering if anyone had any ideas on how to fix these or where should I look to help out getting them fixed.

---

### Post by anish5 on 2015-07-01
Just In case anyone is looking to buy this laptop with Ubuntu pre-installed I found one one ebay [http://www.ebay.com/itm/271918797233?ssPageName=STRK:MEUNSOLD:IT](http://www.ebay.com/itm/271918797233?ssPageName=STRK:MEUNSOLD:IT)

---

### Post by arthur23 on 2015-07-08
Hi all,

I have been using my UX303-LN for 6 months now, quite happy about it, even though multi touch is still not working. I came to understand some guys on this thread solved it, I'd be interested if someone can give relevant materials / tutos / whatever.

What really brings me here  : all day (2 days ago) my laptop was ticking, a lot louder than usual (which makes me suspect its HD related), until most of my processes where kind of frozen, like a memory overflow, except I could type in the terminal and get errors (I could not copy paste nor remember now) for every key I hit (no Enter even needed). I rebooted and got straigthly to the BIOS, no HD found. After 4 or 5 reboots it randomly got to Windows 8.1 (I originally have a dual boot, with Ubuntu as default choice in GRUB). The Secure Boot had been re-enabled, I re-disabled it.

Now I keep on using Ubuntu, but from time to time the ticking starts again, and most of my programs are suddenly unusable, PHPStorm is frozen for instance (except usually Firefox for some reason). If I open up a new terminal, its automatically closed. The ticking can stop, but the system is still buggy until I reboot.

Anyone seen anything related? 

I'd say it's hardware, but it's hard to do it in front of a custome service guy, and since its Linux, they are even less inclined to help. One pretended the warranty ceased the moment I installed Linux. I live in France, I got confirmation some time ago that this is not a legal claim from PC builder and the waranty would still be valid.

Any help appreciated. Thanks

---

### Post by Pilot6 on 2015-07-08
Touchpad solution is at the previous page, if you have a Focatech touchpad.

---

### Post by daniel91090 on 2015-07-22
Hello I am French and I would like to install this Focatech touchpad driver in my Linux (Mageia). Can I install the .deb ? Thank you

---

### Post by Pilot6 on 2015-07-22
Yes, you can install the deb, if you have 3.19 kernel. 3.17-3.18 may work too. I do not remember. I can check.

---

### Post by daniel91090 on 2015-07-22
Thank you Pilot6, you are a great man !! By you, the french users of the zenbook can play with their computer :) In my case, I think Mageia work with rpm :/ and not deb. That is the problem...

---

### Post by Pilot6 on 2015-07-22
That is not a problem at all. You can download source from my github.

```
git clone https://github.com/hanipouspilot/focaltech-dkms.git
sudo cp -r focaltech-dkms /usr/src/focaltech-1.5
sudo rm -r /usr/src/focaltech-1.5/.git
sudo dkms install -m focaltech -v 1.5
```

And you do not need any packages.

---

### Post by neeto2 on 2015-07-27
I can finally use two fingers with my touchpad! I have a little problem with the he clicking area on the touchpad. It's detected as the touch area so when I click the pointer moves slightly, is it supposed to be like this? 
I also can't seem to get the brightness key to work, I tried [COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="[/COLOR]

[COLOR=#000000]and then : update-grub 
[/COLOR]
it generates
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-23-generic
Found initrd image: /boot/initrd.img-3.19.0-23-generic
Found linux image: /boot/vmlinuz-3.16.0-38-generic
Found initrd image: /boot/initrd.img-3.16.0-38-generic
  No volume groups found
Found Windows Boot Manager on /dev/sdb1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done

I have the 303ln broadwell version of this laptop.

Any ideas?

---

### Post by nico-ar on 2015-08-06
Hi! I recently bought a ux303la, I format the ssd and install Ubuntu Mate on it.

- Thanks to Pilot9 (focaltech drivers) I was able to configure the touchpad (scroll gesture and 2/3 finger tap to click). Can I add EdgeMotion property to synclient? (continue dragging movement when reaching the edge of the touchpad) 
- The brightness key doesn't work with the acpi_osi= trick. It's there another way?
- Nor the backlit keys on the keyboard works, but when I press can see the indicator on the screen. And in power-save mode the leds turns off.

small details that would be good to solve, I have not found other.....

---

### Post by wiewiur85 on 2015-08-10
Nico, I have the same computer, and I've tried a lot of combinations to make brightness keys work with no success (Ubuntu is able to change brightness but it doesnt see key presess). I don't know is it posible in Mate but under KDE I simply map different key combination to Brightness+ Brightness- actions (for example Meta+Fx), You can try the same :)

---

### Post by nico-ar on 2015-08-11
> **wiewiur85 said:**
> Nico, I have the same computer, and I've tried a lot of combinations to make brightness keys work with no success (Ubuntu is able to change brightness but it doesnt see key presess). I don't know is it posible in Mate but under KDE I simply map different key combination to Brightness+ Brightness- actions (for example Meta+Fx), You can try the same :)

Yes, I'll do that. I already did something similar for changing the backlit levels.
Thanks!

---

### Post by richtl-dancinglion on 2015-08-31
> **andrzej6 said:**
> I installed 4.0 becouse i had problems with display([http://imgur.com/wFjDRAU](http://imgur.com/wFjDRAU)). On another forum i found info that instaling kernel 4.0 resolve this issue and it did. Why i should not install kernel 4 i read that it is stable?
 
I have everything working well on Ubuntu 15.04 (thanks, Pilot!), but prefer Elementary. However, my Broadwell chip makes the display look exactly as yours did. How did you manage to install Elementary with the GUI looking so completely unreadable?

UPDATED SEPT 8. I just installed the new Elementary 3.1.0 release, and the graphics issue is mostly fixed. There are still graphics glitches in some of the dialogs, but nothing that makes the system unusable. Elementary handles the 3200x display much more elegantly than Ubuntu, btw--no tweaking to deal with microscopic fonts and such. Still hoping for an eventual fix for the brightness keys.

---

### Post by vagemulo on 2015-09-29
I've got a ux303LA with the 3200x1800 display. I'm using linux mint, and even if i adjust fonts and panels, etc, some of the checkboxes are so small I can't even see if they're checked sometimes. But looking at [archwiki]("https://wiki.archlinux.org/index.php?title=Xorg&oldid=373144#Display_size_and_DPI") I discovered that xorg has a completely wrong screen size, nearly a meter instead of 13,3inches! here's the result:

```
xdpyinfo | grep -B2 resolution 
screen #0:
  dimensions:    3200x1800 pixels (847x476 millimeters)
  resolution:    96x96 dots per inch

```

could this be part of the issue with microscopic icons and fonts? supposedly, [Cinnamon deals well with HiDPI]("https://wiki.archlinux.org/index.php/HiDPI"). or should i just install a theme that will make things double size?

I actually calculate that there are 276 DPI:
&#8730;(3200²+1800²)÷13,3=276.052
which means the screen dimensions are:
width:  294mm
heigth: 165mm

A ruler confirms this.

According to the instructions above, I saved a file: /etc/X11/xorg.conf.d/90-monitor.conf
with this:
```
Section "Monitor"
    Identifier             "<default monitor>"
    DisplaySize            294 165    # In millimeters
EndSection

```

and i'll let you know if anything changes when i restart X!


Making the fonts big seems to run into problems with many windows that cannot be adjusted in size.

---

### Post by vagemulo on 2015-09-29
hmm, not sure if that solved much. Chromium stlll looks uncomfortably small.  I am finding my touchpad completely fails on me after a couple of minutes of starting. And simultaneously the touchscreen stops working as it should

---

### Post by nico-ar on 2015-10-22
somebody try ubuntu 15.10 and the 4.x kernel?

---

### Post by HunterSBuntu on 2015-10-24
> **nico-ar said:**
> somebody try ubuntu 15.10 and the 4.x kernel?

Just installed 15.10 on my UX303 this morning.

Two finger scroll now working 'out of the box' on 15.10 w/4.2.0-16 kernel.

Wifi working

Audio working

Keyboard backlight adjustment function keys work,  screen brightness ones do not (as with previous version). To resolve modify follow steps found here under "Function Keys":
[https://wiki.archlinux.org/index.php/ASUS_Zenbook_UX303#Function_Keys](https://wiki.archlinux.org/index.php/ASUS_Zenbook_UX303#Function_Keys)

No complaints. I was on 15.04 before and everything except the touchpad advanced features and the screen brightness keys worked for me straight away.  15.10 seems much the same so far, but with the touchpad two finger features working without an additional install of Pilot6's module.

---

### Post by nico-ar on 2015-10-25
nice, system upgrade or fresh install?

---

### Post by chris377 on 2015-11-03
Hello,

I simply cannot detect an external display. I have tried both the mini DisplayPort and the HDMI , but the fn+f8 functionality simply does not yield any result. Has anyone else had these problems? I am currently running Ubuntu 14.04.3.

---

### Post by Darakt on 2015-12-04
Hi, I have an UX303LN with Ubuntu 15.04.
And I have 2 problems :
I've Never heard the fan
The wifi is quit unreliable.
Any ideas ?

Somes intels :
sudo dmidecode -s bios-version && sudo dmidecode -s bios-release-date
UX303LN.204
09/01/2014
uname -r
3.19.0-37-generic

---

### Post by djtarki on 2016-01-05
> **HunterSBuntu said:**
> Just installed 15.10 on my UX303 this morning.

Two finger scroll now working 'out of the box' on 15.10 w/4.2.0-16 kernel.

Wifi working

Audio working

Keyboard backlight adjustment function keys work,  screen brightness ones do not (as with previous version). To resolve modify follow steps found here under "Function Keys":
[https://wiki.archlinux.org/index.php/ASUS_Zenbook_UX303#Function_Keys](https://wiki.archlinux.org/index.php/ASUS_Zenbook_UX303#Function_Keys)


I'm using a fresh install of 15.10 (kernel 4.2.0-22) on a [FONT=Geneva][SIZE=2]UX303LB-R4109H[/SIZE][/FONT] (2 graphic cards Nvidia and Intel): unfortunately I cannot manage to make the FN brightness keys work as HunterSBuntu suggests.

Any idea?

Thanks.

Note:
> $ sudo dmidecode -s bios-version && sudo dmidecode -s bios-release-date
UX303LB.206
08/24/2015

---

### Post by Tulf on 2016-02-14
I am having trouble getting ubuntu to even boot off a usb so I'm still stuck using windows. I disabled secure boot in Aptio, but whenever I choose my boot location it doesn't seem to recognize the iso file, which has been very frustrating personally. Do you have any basic instruction I should follow when dual booting Ubuntu?

---

### Post by djtarki on 2016-02-18
> **Tulf said:**
> I am having trouble getting ubuntu to even boot off a usb so I'm still stuck using windows. I disabled secure boot in Aptio, but whenever I choose my boot location it doesn't seem to recognize the iso file, which has been very frustrating personally. Do you have any basic instruction I should follow when dual booting Ubuntu?

Try creating the bootable USB with a program different than the one you've used:

[https://duckduckgo.com/?q=create+linux+usb&t=ffsb](https://duckduckgo.com/?q=create+linux+usb&t=ffsb)

Good luck.

---

### Post by GMHilltop on 2016-02-28
First of all my UX303**UB** this has the Skylake processor and a few things seemed to not work compared to the UX303LB version which I also have (but haven't tried this on it yet).
So, to REPEAT: this is for the UX303**_UB_**-DH74T w/ Core i7-6500U, 12GB, 512GB SSD, 13.3in QHD+, GeForce GT 940M

There are 2 things you need to edit in order to get the back Screen Brightness keys to work on the Zenbook UX303UB-DH74T.
This was done with Ubuntu 15.10.
[B]
STEP 1:[/B]

The first is to edit the /etc/default/grub file

Go into Terminal and type:

```
sudo gedit /etc/default/grub
```

and change the line that says:
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
        to
    GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="

and then : ```
sudo update-grub
```

**ALSO NOTE:**  If you do ONLY this, the slider will show up, but the screen brightness won't change.  
You MUST do step 2 to to get it to work!

**STEP2:**

This worked for intel based systems.  
You can verify you have an intel setup by opening terminal and typing:

    ```
ls /sys/class/backlight/
```
    
My system replied with:
    acpi_video0  intel_backlight
    
Then you have to create a file (this was not in my system) by typing:

    ```
sudo gedit /usr/share/X11/xorg.conf.d/20-intel.conf
```
    
. . . and put this info into it:


```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```


Everything should work just fine after that.

---

### Post by djtarki on 2016-03-18
> **GMHilltop said:**
> First of all my UX303**UB** this has the Skylake processor and a few things seemed to not work compared to the UX303LB version which I also have (but haven't tried this on it yet).

I've tried my UX303LB with the same steps you described and it did not work (not even a slider shown)

If you manage to make it work post it here please.

Thanks anyway!

---

### Post by foxy123 on 2016-05-30
Hi, how does it work now with Ubuntu 16.04? Any major issues? I am considering to buy it but if there are still issues I would probably buy UX305CA, which is cheaper and as I heard works well with Ubuntu.

---

### Post by djtarki on 2016-05-31
> **foxy123 said:**
> Hi, how does it work now with Ubuntu 16.04? Any major issues? I am considering to buy it but if there are still issues I would probably buy UX305CA, which is cheaper and as I heard works well with Ubuntu.

Ubuntu 16.04 has the same problems as 15.10 on my side regarding the FN keys for backlight control. Besides, I'm experiencing [problems with NVIDIA drivers]("http://askubuntu.com/questions/761136/ubuntu-16-04-nvidia-drivers-dont-work/761356#761356").

Anyway, in general terms it works fine for my Asus UX303LB 

Best regards.

---

### Post by foxy123 on 2016-05-31
> **djtarki said:**
> Ubuntu 16.04 has the same problems as 15.10 on my side regarding the FN keys for backlight control. Besides, I'm experiencing [problems with NVIDIA drivers]("http://askubuntu.com/questions/761136/ubuntu-16-04-nvidia-drivers-dont-work/761356#761356").

Anyway, in general terms it works fine for my Asus UX303LB 

Best regards.

Thanks a lot for the response. BTW, is it a fanless laptop?

---

### Post by djtarki on 2016-05-31
No, it's not. However, at normal use (no videos or games) you can barely notice the fan.... I truly recommend this laptop.

Best regards.

---

### Post by shaan2 on 2016-06-09
Hi, there , I am also using asus ux303ub laptop, after little bit of experiment , I got the solution,   to solve **screen brightness adjustment** and keyboard backlight issue just add acpi_backlight=none acpi_osi= 
to GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub and you are good to go.......

Your grub file will be like this....



# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=none acpi_osi="
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)

Dont forget to update grub after adding the kernel parameter, to do that
 
run command update-grub in terminal........


Hope it helps....

---

### Post by djtarki on 2016-06-11
Hi shaan2,

I've done:

1) Edited my /etc/default/grub. It looks like this now:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
#GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=none acpi_osi="
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

```

2) Save it and run sudo update-grub

3) Restarted the laptop

Still, **my brightness keys (fn+f5/f6) won't work**.

My laptop is an Asus UX303LB (Intel + Nvicia 940M graphic cards).

Any idea?

Thanks a lot!

---

### Post by shaan2 on 2016-06-18
Hi there,
 Try using 
acpi_backlight=native in place of acpi_backlight=none

---

### Post by djtarki on 2016-06-19
> **shaan2 said:**
> Hi there,
 Try using 
acpi_backlight=native in place of acpi_backlight=none

I've just tried that. After editing the file, update-grub and reboot nothing changed. I can still tune the brightness using the "Brighness & lock" option in Ubuntu but my FN F4/F5 keys won't work.

Thanks anyway shaan2!

---

### Post by Bernd_Hentig on 2016-06-22
> **shaan2 said:**
> Hi there,
 Try using 
acpi_backlight=native in place of acpi_backlight=none


There are different generations of the ASUS Zenbook and depending on the BIOS, Fn5/6 will work or not.
So far I have found out this:

Gen4    (UX303LA + UX303LN with Intel Haswell i5-4210U, i7-4500 etc.)             
acpi_osi=
makes Fn5/Fn6 + wireless switch work (keyboard backlight works out of the box)

Gen5    (UX303LA+UX303LB with Intel Broadwell i5-5200U, i7-5500U etc.)
Fn5/Fn6 will not generate an ACPI event or deliver any keycodes due to driver error in Intel ACPI code (will probably never be fixed, so you have to find another key for your backlight scripts)
Keyboard backlight works out of the box
wireless switch still needs "acpi_osi=" kernel parameter

Gen6    (UX303UA+UX303UB with Intel Skylake i5-6200U, i7-6500U etc.)
acpi_osi=  acpi_backlight=native
makes Fn5/Fn6 + wireless switch work (keyboard backlight works out of the box)

What makes me wonder is that most Lenovo and HP notebooks do not have this problem, the Fn-keys mostly just work.
And what annoys me even more is, the keyboard backlight keys on the Zenbooks just work - it is absolutely ridiculous that the panel backlight does not, something is heavily broken here either in the kernel or in the BIOS - maybe both ends. And it is nearly impossible to trace or debug this stuff if you are not a kernel developer.
It is always ASUS and sometimes Acer notebooks that show problems with keyboard and panel backlight, as well as multiple problems with Wifi switch and corresponding LED indicator.
So there should be found a simple and one-for-all fix.

For the 5th gen notebooks, nearly all ASUS and ACER models show the same bug, the Fn5/Fn6 keys do not generate any ACPI event in Linux - although they work flawlessly in Win7,8 and 10.
If anybody knows how to make Fn5/Fn6 generate an ACPI event or at least a keycode that could be mapped to some nifty shell script, please let us know.
There are thousands of Linux users out there that would benefit from this 8-)

---

### Post by djtarki on 2016-06-22
Thanks a lot for the explanation, it's been very enlightening! :)

So, for us, proud owners of the Gen5 notebooks (UX303LA+UX303LB), the only hope is that someone provides a fix to solve this situation of not delivering any key codes because of the Intel driver.... let's see if that happens... :popcorn:

BR

---

