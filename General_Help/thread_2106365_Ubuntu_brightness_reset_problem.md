---
title: "Ubuntu brightness reset problem"
date: 2013-01-18
forum: General Help
---

### Post by c2tarun on 2013-01-18
Hi friends,

I am using Ubuntu 12.04. The problem I am facing is each time I reboot my brightness is set to Maximum.

I tried solution from ask.ubuntu : [http://askubuntu.com/questions/151651/brightness-is-reset-to-maximum-on-every-restart](http://askubuntu.com/questions/151651/brightness-is-reset-to-maximum-on-every-restart)

Here is my rc.local

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

echo 7 > /sys/class/backlight/acpi_video0/brightness
touch /home/tarun/testingrclocal
exit 0

```

Nothing is happening. I also tried to edit "/sys/class/backlight/acpi_video0/brightness" file manually but I don't have access. I added a touch command in rc.local just to see whether it is working or not, rc.local is fine :( its just my brightness not changing. Can anyone please help.

---

### Post by helpee on 2013-01-18
Did you edit it with sudo privileges or as a regular user?

Also, why didn't you add the same line as in your link?

"/sys/class/backlight/intel_backlight/brightness"
instead of your path
"/sys/class/backlight/acpi_video0/brightness"

---

### Post by offgridguy on 2013-01-18
Thanks for the link, it may come in handy.

---

### Post by c2tarun on 2013-01-20
> **helpee said:**
> Did you edit it with sudo privileges or as a regular user?
Dude you could have guessed that by looking at the fact that, I already edited rc.local. This file can't be edited without root privileges ;)

> Also, why didn't you add the same line as in your link?

"/sys/class/backlight/intel_backlight/brightness"
instead of your path
"/sys/class/backlight/acpi_video0/brightness"

There is no link (no intel_backlight folder). And even if there is a link, since its a link I think that adding entries at both places is kind of against the concept of link.

---

### Post by c2tarun on 2013-01-20
> **offgridguy said:**
> Thanks for the link, it may come in handy.

You're welcome.
If your machines brightness hurting your eyes, try this: [http://stereopsis.com/flux/](http://stereopsis.com/flux/)

---

### Post by c2tarun on 2013-01-23
I still didn't find the solution, my last post was just a work around, still I want to lower brightness of my laptop.

Bump...

---

### Post by Toz on 2013-01-23
What is the make and model of your computer?

What video card and driver are you using?
```
sudo lspci -vnn | grep -A12 VGA
```

What backlight interfaces do you have?
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
```

What says dmesg?
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.

---

### Post by c2tarun on 2013-01-23
> **Toz said:**
> What is the make and model of your computer?

Dell Inspiron N4010

> What video card and driver are you using?
```
sudo lspci -vnn | grep -A12 VGA
```


```
02:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5400 Series] [1002:68e0] (prog-if 00 [VGA controller])
	Subsystem: Dell Device [1028:0456]
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at cfee0000 (64-bit, non-prefetchable) [size=128K]
	I/O ports at 2000 [size=256]
	[virtual] Expansion ROM at cfe00000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 3
	Capabilities: [58] Express Legacy Endpoint, MSI 00
	Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
	Kernel driver in use: fglrx_pci
	Kernel modules: fglrx, radeon

```


> What backlight interfaces do you have?
acpi_video0
> ```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/actual_brightness; cat $interface/max_brightness; done
```
I am not getting anything on "echo $interface"

max_brightness = 15
actual_brightness = 15

> What says dmesg?
[http://paste.ubuntu.com/1563218/](http://paste.ubuntu.com/1563218/)


> ```
pastebinit /var/log/dmesg
```
...and post back the link that is generated.
[http://paste.ubuntu.com/1563222/](http://paste.ubuntu.com/1563222/)

---

### Post by Toz on 2013-01-23
Do the following commands affect brightness for you?
```
echo 5 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
```
echo 10 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
```
echo 15 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

Can you try the following kernel boot parameter:
**acpi_osi=Linux acpi_backlight=vendor** 
(exactly as that, don't change the word vendor to anything). See [here]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") for information on how to temporarily test kernel parameters. With these parameters, do your function keys work?

From your dmesg log file:
> [   28.317898] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
Can you also try the **acpi_osi=** kernel boot parameter?

When you are testing the kernel boot parameters and you boot into your system with those parameters active, can you save a copy of the results of this command:
```
cat /proc/cmdline
```
...so that we can confirm that the proper parameters were entered?

---

### Post by c2tarun on 2013-01-23
> **Toz said:**
> Do the following commands affect brightness for you?
```
echo 5 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
```
echo 10 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
```
echo 15 | sudo tee /sys/class/backlight/acpi_video0/brightness
```


This worked, and I also added these lines to rc.local and now when I reboot my brightness is getting reduced.

Actually there are keys to change the brightness, but when I change it my system crashes. Please look at this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1007765](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1007765)
Wow, I looked at the activity log today they fixed the problem in post #71. :) I am going to try it.

BTW thanks a lot Toz

---

### Post by Timpster on 2013-01-23
WOAH WOAH WHOA

what you need is redshift

install redshift from the Ubuntu repository
sudo apt-get install redshift

then do the command below

redshift -t 6000:4500 -g 0.55

the 4500 you can change and make the screen more or less orange
up makes it more blue and down makes it more orange

the -g changes the gamma which is .55 or half gamma i guess

check it out it may just solve all your problems
oh and ONLY use the NIGHT (4500) at NIGHT TIME
do not make the screen red in the daytime DO NOT make the screen red in the day time got it?

Ok enjoy :popcorn:

---

### Post by c2tarun on 2013-01-24
> **Timpster said:**
> WOAH WOAH WHOA

what you need is redshift

install redshift from the Ubuntu repository
sudo apt-get install redshift

then do the command below

redshift -t 6000:4500 -g 0.55

the 4500 you can change and make the screen more or less orange
up makes it more blue and down makes it more orange

the -g changes the gamma which is .55 or half gamma i guess

check it out it may just solve all your problems
oh and ONLY use the NIGHT (4500) at NIGHT TIME
do not make the screen red in the daytime DO NOT make the screen red in the day time got it?

Ok enjoy :popcorn:

I already have f.lux which kind of does what redshift does :) and it just changes the color depth and make it soothing, but brightness is still at max, which hurt eyes a lot.

---

### Post by Toz on 2013-01-24
> **c2tarun said:**
> Please look at this bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1007765](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1007765)
Wow, I looked at the activity log today they fixed the problem in post #71. :) I am going to try it.

Does the suggestion from post #71 work for you?

---

### Post by c2tarun on 2013-01-24
> **Toz said:**
> Does the suggestion from post #71 work for you?

Yeah it worked :)
I am marking this thread as solved.

---

