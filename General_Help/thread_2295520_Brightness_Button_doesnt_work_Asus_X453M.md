---
title: "Brightness Button doesnt work Asus X453M"
date: 2015-09-19
forum: General Help
---

### Post by anonprophet on 2015-09-19
im already google how to fix it

i got solution like this

[COLOR=#111111][FONT=Ubuntu]In the terminal:[/FONT][/COLOR]
```

[LIST=1]
[*]sudo gedit /etc/default/grub
Change
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi="
Then, save the file. 
[*]sudo update-grub 
[*]Restart computer. 
[/LIST]

```

i just see the brightness indicator now , but the brightness not change
and change from System Settings -> Brightness and Lock will not change too

Ubuntu 14.04.3 LTS 64bit

---

### Post by nknwn on 2015-09-19
**acpi_osi=**

acpi_osi equals what? 
Anyway I hesitate to advise on editing grub as I recently had a bad experience with grub :)

You can of course change brightness in System Settings > brightness and lock

---

### Post by Frogs Hair on 2015-09-19
Some brightness control work-arounds target specific graphics cards. Post the output if the following. ```
lspci
```

---

### Post by anonprophet on 2015-09-20
> **Frogs Hair said:**
> Some brightness control work-arounds target specific graphics cards. Post the output if the following. ```
lspci
```

```

00:00.0 Host bridge: Intel Corporation ValleyView SSA-CUnit (rev 0e)
00:02.0 VGA compatible controller: Intel Corporation ValleyView Gen7 (rev 0e)
00:13.0 SATA controller: Intel Corporation ValleyView 6-Port SATA AHCI Controller (rev 0e)
00:1a.0 Encryption controller: Intel Corporation ValleyView SEC (rev 0e)
00:1b.0 Audio device: Intel Corporation ValleyView High Definition Audio Controller (rev 0e)
00:1c.0 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1c.1 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1c.3 PCI bridge: Intel Corporation ValleyView PCI Express Root Port (rev 0e)
00:1d.0 USB controller: Intel Corporation ValleyView USB Enhanced Host Controller (rev 0e)
00:1f.0 ISA bridge: Intel Corporation ValleyView Power Control Unit (rev 0e)
00:1f.3 SMBus: Intel Corporation ValleyView SMBus Controller (rev 0e)
02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5286 (rev 01)
03:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 06)

```

---

### Post by anonprophet on 2015-09-20
> **nknwn said:**
> **acpi_osi=**

acpi_osi equals what? 
Anyway I hesitate to advise on editing grub as I recently had a bad experience with grub :smile:

You can of course change brightness in System Settings > brightness and lock


i try use acpi_osi=vendor
its not work too :(

i dont know what im doing, but now change brightness in System Settings > Brightness and Lock not working
EDIT : not working bcoz acpi_osi

---

### Post by nknwn on 2015-09-20
There's an argument over here: [http://askubuntu.com/questions/28848/what-does-the-kernel-boot-parameter-set-acpi-osi-linux-do](http://askubuntu.com/questions/28848/what-does-the-kernel-boot-parameter-set-acpi-osi-linux-do) 
Saying it should be **acpi_osi=Windows** as opposed to **acpi_osi=Linux** 

It's up to you if you want to try it ;)

---

### Post by Frogs Hair on 2015-09-20
```
VGA compatible controller: Intel Corporation ValleyView Gen7 (rev 0e)
``` I used the following in 14.04 after installing the Gnome Shell as a second desktop, but what ever caused the problem was not an issue in later releases. [http://itsfoss.com/fix-brightness-ubuntu-1310/](http://itsfoss.com/fix-brightness-ubuntu-1310/)

If it doesn’t work just open and delete the contents of the file.

---

### Post by anonprophet on 2015-09-20
> **Frogs Hair said:**
>  [http://itsfoss.com/fix-brightness-ubuntu-1310/](http://itsfoss.com/fix-brightness-ubuntu-1310/)

its doesnt work for me

> **nknwn said:**
> There's an argument over here: [http://askubuntu.com/questions/28848/what-does-the-kernel-boot-parameter-set-acpi-osi-linux-do](http://askubuntu.com/questions/28848/what-does-the-kernel-boot-parameter-set-acpi-osi-linux-do) 
Saying it should be **acpi_osi=Windows** as opposed to **acpi_osi=Linux** 

already try it, doesnt work too

---

### Post by anonprophet on 2015-09-22
bump,
still need help here

and brightness settings (not remember) reset  too full every restart.

---

### Post by Toz on 2015-09-22
A couple of things come to mind:

1. Depending on the kernel version you are using, you may need to use the **video.use_native_backlight=1** instead of "acpi_backlight=vendor"
2. Maybe the kernel you are using doesn't have full support for the valleyview chipset (I tried to help another member with a similar chipset and 14.04 [here]("http://ubuntuforums.org/showthread.php?t=2250862")).

Can you confirm some information:

1. The kernel version you are using:
```
uname -a
```

2. Your current kernel boot line:
```
cat /proc/cmdline
```

3. Info about the recognized backlight interfaces:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```

4. What, if anything, xorg says about backlight:
```
cat /var/log/Xorg.0.log | grep -i backlight
```

---

### Post by nknwn on 2015-09-22
Neither Ubuntu 14.04 or Lubuntu 14.04.3 remember my brightness settings but that is not a problem on this laptop as they both enable the brightness buttons.

In the absence of a solution for you buttons here's what I recommend:

From the Ubuntu software centre install [B]xbacklight
[/B]You can then change the brightness by running the command **xbacklight = 60 **in the Terminal where 60 is 60% brightness.

But it would be better if you had a script file which when double clicked set your preferred brightness IMO.

Open up gedit the text editor and enter:

[B]#!/bin/bash 
xbacklight = 60

[/B]Save the file with an appropriate name such a 'mydimmer.sh' or whatever you prefer it doesn't need a filename extension.
Now right click on the file, choose properties and select execute in the permissions.

One more setting - this is system wide.
From the menu bar when a directory/folder is maximized choose [B]edit > Preferences > Behaviour > run executable text files when they are opened > close


[/B]Now you can double click on your script file to set the brightness you prefer[B].


[/B]

---

### Post by anonprophet on 2015-09-23
anonprophet@anonbook:~$ uname -a
```

Linux anonbook 3.19.0-28-generic #30~14.04.1-Ubuntu SMP Tue Sep 1 09:32:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

```

anonprophet@anonbook:~$ cat /proc/cmdline 
```

BOOT_IMAGE=/boot/vmlinuz-3.19.0-28-generic.efi.signed root=UUID=aedfc7ac-79f1-40ab-8c5b-dcca1fa93245 ro quiet splash acpi_osi=Linux vt.handoff=7

```

anonprophet@anonbook:~$ for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```

 /sys/class/backlight/intel_backlight
3046
7812
3046

```

anonprophet@anonbook:~$ cat /var/log/Xorg.0.log | grep -i backlight
```

[    21.343] (**) intel(0): Option "Backlight" "intel_backlight"
[    21.344] (**) intel(0): Found backlight control interface intel_backlight (type 'raw') for output eDP1

```

---

### Post by Toz on 2015-09-23
Do the following commands change your brightness level (you will need to enter your password):
```
echo 7812 | sudo tee /sys/class/backlight/intel_backlight/brightness
echo 3046 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

Does the brightness slider work?

Do the brightness keyboard combinations work?

---

### Post by anonprophet on 2015-09-27
> **Toz said:**
> Do the following commands change your brightness level (you will need to enter your password):
```
echo 7812 | sudo tee /sys/class/backlight/intel_backlight/brightness
echo 3046 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

Does the brightness slider work?

Do the brightness keyboard combinations work?

1. the command work
2. brightness slider in Settings work
3. if u mean Fn + F5 and Fn + F6 its doesnt work

sorry for late reply

---

### Post by Toz on 2015-09-27
So it's just the keyboard shortcuts that don't work.

Two things to try:

1. In a terminal window, run:
```
xev | sed -n 's/^.*state \([0-9].*\), keycode *\([0-9]\+\) *\(.*\), .*$/keycode \2 = \3, state = \1/p'
```
...then press Fn+F5 and Fn+F6. Post back any messages that appear in the terminal window.

2. In a terminal window, run:
```
acpi_listen
```
...then press Fn+F5 and Fn+F6. Post back any messages that appear in the terminal window.

---

### Post by anonprophet on 2015-09-27
nothing showed up if press fn+f5 & fn+f6
but if i press fn+f11 / fn+f12 (lower and raise volume) like this

1.
```

keycode 122 = (keysym 0x1008ff11, XF86AudioLowerVolume), state = 0x0
keycode 123 = (keysym 0x1008ff13, XF86AudioRaiseVolume), state = 0x0

```

2.
```

button/volumedown VOLDN 00000080 00000000 K
button/volumeup VOLUP 00000080 00000000 K

```

---

### Post by Toz on 2015-09-27
Your system isn't recognizing your function hotkeys. Earlier you tried "acpi_osi=" (which btw is a valid kernel parameter). Can you try the following grub parameters:
```
acpi_osi= acpi_backlight=vendor
```

Once booted into your system, can you post back the results of:
1. Kernel boot line:
```
cat /proc/cmdline
```
2. Recognized backlight interfaces:
```
for interface in /sys/class/backlight/*; do echo -e "\n $interface"; cat $interface/{brightness,max_brightness,actual_brightness}; done
```
3. And try both:
```
xev | sed -n 's/^.*state \([0-9].*\), keycode *\([0-9]\+\) *\(.*\), .*$/keycode \2 = \3, state = \1/p'
```
...and:
```
acpi_listen
```
...again to see if you get a response.

---

### Post by anonprophet on 2015-09-27
1.
```

BOOT_IMAGE=/boot/vmlinuz-3.19.0-28-generic.efi.signed root=UUID=aedfc7ac-79f1-40ab-8c5b-dcca1fa93245 ro quiet splash acpi_osi= acpi_backlight=vendor vt.handoff=7

```

2.
```

 /sys/class/backlight/asus-nb-wmi
10
10
10

 /sys/class/backlight/intel_backlight
2343
7812
2343

```

3. Nothing Show Up even though FN + F11 / F12 (all combination with FN not work)

4.
FN + F5
```

 PNP0C14:00 000000ff 00000000

```

FN + F6
```

 PNP0C14:00 000000ff 00000000

```


This command and brightness slider in settings work
```

echo 7812 | sudo tee /sys/class/backlight/intel_backlight/brightness
echo 3046 | sudo tee /sys/class/backlight/intel_backlight/brightness

```

---

### Post by Toz on 2015-09-27
Try this combination in your /etc/default/grub file instead:
```
acpi_osi=\"! Windows 2012\" acpi_backlight=vendor
```
...and post back the results as before.

---

### Post by anonprophet on 2015-09-27
```

BOOT_IMAGE=/boot/vmlinuz-3.19.0-28-generic.efi.signed root=UUID=aedfc7ac-79f1-40ab-8c5b-dcca1fa93245 ro quiet splash "acpi_osi=! Windows 2012" acpi_backlight=vendor vt.handoff=7

```

```

 /sys/class/backlight/asus-nb-wmi
100
100
100

 /sys/class/backlight/intel_backlight
2343
7812
2343

```

3 & 4 Nothing Show for FN + F5/F6

---

### Post by nknwn on 2015-09-27
While playing around with **acpi_listen **I find that the **PRT SC** key returns nothing to the terminal and does not take a screen capture as it should. However, when I press **ALT **and **PRT SC** then release **PRT SC** and **ALT** in that order the screen capture occurs. Still nothing is written to the terminal. 

This is something to try but with the brightness if it has not already been tried.

---

### Post by Toz on 2015-09-27
> **anonprophet said:**
> ```

BOOT_IMAGE=/boot/vmlinuz-3.19.0-28-generic.efi.signed root=UUID=aedfc7ac-79f1-40ab-8c5b-dcca1fa93245 ro quiet splash "acpi_osi=! Windows 2012" acpi_backlight=vendor vt.handoff=7

```

```

 /sys/class/backlight/asus-nb-wmi
100
100
100

 /sys/class/backlight/intel_backlight
2343
7812
2343

```

3 & 4 Nothing Show for FN + F5/F6
Oops. Typo. Try this one instead:
```
acpi_osi=\"!Windows 2012\" acpi_backlight=vendor
```
...(no space between the ! and the W).

If that doesn't work, try this alternate form:
```
acpi_osi='!Windows 2012' acpi_backlight=vendor
```

---

### Post by anonprophet on 2015-11-23
sorry for very very very late reply

im already try both, but its still not work.

---

