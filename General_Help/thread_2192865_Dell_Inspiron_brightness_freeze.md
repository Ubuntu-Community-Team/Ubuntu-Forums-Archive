---
title: "Dell Inspiron brightness freeze"
date: 2013-12-10
forum: General Help
---

### Post by TehNanor on 2013-12-10
I've ran into a strange bug on my install of Ubuntu. I'm running Ubuntu 13.10 on a Dell Inspiron 15 with hybrid graphics consisting of an ATI Radeon 7730M and an Intel Graphics 4000 card. I noticed that when I left my computer on idle and the screen locked and went black I was completely unable to wake it. I couldn't CTRL + ALT + F2 into another TTY and it required a hard reset. I thought this was strange so I tried to go to my options and turn off the lock in the Brightness & Lock settings. Whenever I clicked the icon the computer froze in the exact same manner.

I've read on a few places that brightness problems are common on Dell Inspirons. Is anybody able to shed some light on my problem?

---

### Post by Toz on 2013-12-10
Some more detailed information would be helpful (open a terminal window, enter the command and post back the results):
1. Your current kernel boot command line:
```
cat /proc/cmdline
```

2. Info about your video cards and drivers:
```
lspci -k | grep -iA3 VGA
```

3. Your backlight interfaces and values:
```
for i in /sys/class/backlight/*; do echo $i;cat $i/brightness;cat $i/max_brightness;done
```

---

### Post by TehNanor on 2013-12-10
Here's the information you requested in order.

> rony@comet:~/Downloads$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.11.0-14-generic.efi.signed root=UUID=ea92fb00-0dfc-465f-bcdd-a53d414ff5cb ro quiet splash pcie_aspm=force acpi_backlight=vendor vt.handoff=7


> rony@comet:~/Downloads$ lspci -k | grep -iA3 VGA
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
    Subsystem: Dell Device 0572
    Kernel driver in use: i915
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
--
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Chelsea LP [Radeon HD 7730M]
    Subsystem: Dell Device 0572
    Kernel driver in use: fglrx_pci
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)


> 
rony@comet:~/Downloads$ for i in /sys/class/backlight/*; do echo $i;cat $i/brightness;cat $i/max_brightness;done
/sys/class/backlight/dell_backlight
15
15
/sys/class/backlight/intel_backlight
4882
4882


Let me know if you need anything more.

---

### Post by Toz on 2013-12-10
I see you've already got the proprietary drivers installed. How did you setup the switchable graphics? Are you currently using the intel or Ati card?

Do brightness controls work for you?

Out of curiosity, which of the following backlight interfaces work (which commands adjust the backlight)?
```
echo 7 | sudo tee /sys/class/backlight/dell_backlight
echo 15 | sudo tee /sys/class/backlight/dell_backlight
```
...OR
```
echo 2441 | sudo tee /sys/class/backlight/intel_backlight
echo 4882 | sudo tee /sys/class/backlight/intel_backlight
```

Would be interested in seeing your Xorg log file:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

---

### Post by TehNanor on 2013-12-10
I installed Catalyst Control Center which tells me I'm using the ATI card and seemed to set everything up. Neither of those commands do anything. Entering them gave me this:

> 
rony@comet:~$ echo 7 | sudo tee /sys/class/backlight/dell_backlight
[sudo] password for rony: 
tee: /sys/class/backlight/dell_backlight: Is a directory
7
rony@comet:~$ echo 7 | sudo tee /sys/class/backlight/dell_backlight
tee: /sys/class/backlight/dell_backlight: Is a directory
7
rony@comet:~$ echo 15 | sudo tee /sys/class/backlight/dell_backlight
tee: /sys/class/backlight/dell_backlight: Is a directory
15
rony@comet:~$ echo 2441 | sudo tee /sys/class/backlight/intel_backlight
tee: /sys/class/backlight/intel_backlight: Is a directory
2441
rony@comet:~$ echo 4882 | sudo tee /sys/class/backlight/intel_backlight
tee: /sys/class/backlight/intel_backlight: Is a directory
4882


[Here](http://paste.ubuntu.com/6551439) is a pastebin of my xorg logs.

---

### Post by Toz on 2013-12-10
> **TehNanor said:**
> I installed Catalyst Control Center which tells me I'm using the ATI card and seemed to set everything up. Neither of those commands do anything. Entering them gave me this:
Sorry, my bad. try these commands instead:
```

echo 7 | sudo tee /sys/class/backlight/dell_backlight/brightness
echo 15 | sudo tee /sys/class/backlight/dell_backlight/brightness
```
...OR
```

echo 2441 | sudo tee /sys/class/backlight/intel_backlight/brightness
echo 4882 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

> [Here](http://paste.ubuntu.com/6551439) is a pastebin of my xorg logs.
Thanks, I'll have a look.

---

### Post by TehNanor on 2013-12-10
Running the first command froze the computer entirely requiring a hard reset.

EDIT: Was the first command meant to turn down the brightness? When I rebooted my laptop screen seems a little darker.

---

### Post by Toz on 2013-12-10
> **TehNanor said:**
> Running the first command froze the computer entirely requiring a hard reset.

EDIT: Was the first command meant to turn down the brightness? When I rebooted my laptop screen seems a little darker.

Yes and very interesting. What kernel modules do you have running? There should be at least one dell one:
```
lsmod | grep -i dell
```

This kernel module would provide the dell_backlight interface and if it is causing the freezing, perhaps we can configure or remove it.

---

### Post by TehNanor on 2013-12-11
> **Toz said:**
> lsmod | grep -i dell

That gives me the following:

```

rony@comet:~$ lsmod | grep -i dell
dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
dell_laptop            17369  0 
dcdbas                 14847  1 dell_laptop
wmi                    19070  1 dell_wmi

```

---

### Post by Toz on 2013-12-11
Try blacklisting the dell_laptop module by adding:
```
blacklist dell_laptop
```
...to the end of the **/etc/modprobe.d/blacklist.conf** file and rebooting.

On reboot, post back again:
```
lsmod
```
```
for i in /sys/class/backlight/*; do echo $i;cat $i/brightness;cat $i/max_brightness;done
```
...and try adjusting the brightness. Also let the computer idle out and see what happens.

---

### Post by TehNanor on 2013-12-11
[The results of lsmod]("http://pastebin.com/N7BZjfnV"). The for loop gives me:
> 
/sys/class/backlight/intel_backlight
2431
4882


Going to try the brightness and idling thing now.

---

### Post by TehNanor on 2013-12-11
It works! Fantastic, thank you! What was the problem? Was there a conflict between two things trying to use the brightness settings at once?

---

### Post by Toz on 2013-12-11
> **TehNanor said:**
> It works! Fantastic, thank you! What was the problem? 
It would appear that for your laptop, the dell_laptop kernel module is interfering with and incorrectly managing the backlight interface. 
> Was there a conflict between two things trying to use the brightness settings at once?
Its more like the dell backlight interface was taking precedence and was causing a problem. Perhaps related to the fact that you have a switchable graphics sub-system.

I'm glad its solved for you. If you don't mind, can you mark this thread as SOLVED from the "Thread Tools" link at the top of the page so that others with the same problem can more easily find this thread? Thanks.

---

