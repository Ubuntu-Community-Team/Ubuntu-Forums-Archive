---
title: "Set default screen brightness on Lenovo X220"
date: 2013-05-10
forum: General Help
---

### Post by epikvision on 2013-05-10
I run Ubuntu 13.04 stable on my Thinkpad X220. One thing that has been bugging me is that the brightness always resets to full with every startup.  I've also been searching for similar issues around the forum, but they go back to older versions of Ubuntu.  Another trend I noticed was that setting the brightness varies between machines.

Is there a way to adjust the screen brightness, so that every restart will keep my screen at current, in-session brightness? I'm guessing it involves editing grub.

---

### Post by Toz on 2013-05-11
Try using the **acpi_osi="!Windows 2012"** kernel parameter.

Edit **/etc/default/grub** as root, and change:
```
GRUB_CMDLINE_LINUX=""
```
...to read:
```
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""
```

Save the file then run:
```
sudo update-grub
```
...and reboot.

---

### Post by epikvision on 2013-05-11
I did that, but after reboot, my screen is still back to 100% brightness at the login screen. 

Can you explain why we need to set 'Windows 7' as a parameter?  Is it because the laptop was once a Windows 7 machine?

---

### Post by Toz on 2013-05-11
There was a change in kernel 3.8 to deal with the way that Windows 8 deals with brightness. As I understand it, the acpi brightness values were reversed??. This particular parameter tells the bios that the O/S is not Windows 8.

Can you try **acpi_backlight=vendor** (use vendor backlight controls, not acpi controls) instead? If that doesn't work, you might want to try **acpi_osi=** (don't report an O/S to the bios).

References: 
- [http://msdn.microsoft.com/en-us/library/windows/hardware/jj159305.aspx]("http://msdn.microsoft.com/en-us/library/windows/hardware/jj159305.aspx")
- [https://bbs.archlinux.org/viewtopic.php?id=147804]("https://bbs.archlinux.org/viewtopic.php?id=147804") (specifically post #18)

---

### Post by epikvision on 2013-05-17
Sorry for the late reply, but neither of those solutions have worked for me.  I still have full backlight after reboot.

---

### Post by Toz on 2013-05-17
Can you post back the results of the following commands:

1. What video card(s) do you have:
```
sudo lspci -vnn | grep -A12 VGA
```
2. What kernel parameters are you currently using:
```
cat /proc/cmdline
```
3. What backlight interfaces do you have:
```
for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/max_brightness; done
```

---

### Post by epikvision on 2013-05-17
My graphics card.
```

john@kotux:~$ sudo lspci -vnn | grep -A12 VGA
[sudo] password for john: 
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device [17aa:21da]
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 6000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915

00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04) 
```

Kernel parameters
```

john@kotux:~$ cat /proc/cmdline
BOOT_IMAGE=/vmlinuz-3.9.0-2-generic root=/dev/mapper/ubuntu--vg-root ro acpi_osi= quiet splash vt.handoff=7 
```

Backlight
```

john@kotux:~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/max_brightness; done
/sys/class/backlight/acpi_video0
5
15
/sys/class/backlight/intel_backlight
4648
4648 
```

---

### Post by Toz on 2013-05-17
Why are you using the **acpi_osi=** kernel prameter? Does it fix an issue for you?

Can you remove the **acpi_osi=** kernel parameter, add the **acpi_backlight=vendor** kernel parameter, reboot, then post back the results of those commands again? And also check brightness.

---

### Post by epikvision on 2013-05-18
**Graphics card.**
```

john@kotux:~$ sudo lspci -vnn | grep -A12 VGA
[sudo] password for john:
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device [17aa:21da]
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 6000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915

00:16.0 Communication controller [0780]: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 [8086:1c3a] (rev 04)

```

**Kernel parameters**
```

john@kotux:~$ cat /proc/cmdline
BOOT_IMAGE=/vmlinuz-3.9.0-2-generic root=/dev/mapper/ubuntu--vg-root ro acpi_backlight=vendor quiet splash vt.handoff=7

```
When I made the change, changing brightness with the brightness keys behave abnormally. The notifications for changing brightness is static, but the function keys work; The brightness is still full.

**Backlight**
```

john@kotux:~$ for interface in /sys/class/backlight/*; do echo $interface; cat $interface/brightness; cat $interface/max_brightness; done
/sys/class/backlight/acpi_video0
6
15
/sys/class/backlight/intel_backlight
4648
4648

```
Perhaps, the problem is in here?  Do I have to modify something?

---

### Post by epikvision on 2013-05-18
For my kernel parameters, both "acpi_osi=" and "acpi_osi=\"!Windows 2012\"" function properly but still yield max brightness at reboot.  The "acpi_backlight=vendor" doesn't really.

---

### Post by Toz on 2013-05-19
Okay. Which of the following commands affect brightness?
```
echo 15 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
```
echo 6 | sudo tee /sys/class/backlight/acpi_video0/brightness
```
```
echo 2324 | sudo tee /sys/class/backlight/intel_backlight/brightness
```
```
echo 4648 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

---

### Post by epikvision on 2013-05-19
The following commands affected me this way...

**Maximized brightness.**
```
 echo 15 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

O.O -** Set to current brightness**
```
 echo 6 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

I guess the best I can do is have the computer start at optimal brightness, not where I left off.

---

### Post by Toz on 2013-05-20
> **epikvision said:**
> 
I guess the best I can do is have the computer start at optimal brightness, not where I left off.

To do so, edit **/etc/rc.local** and above the *exit 0* command, add the line:
```
echo 6 > /sys/class/backlight/acpi_video0/brightness
```

---

### Post by epikvision on 2013-05-20
> **Toz said:**
> To do so, edit **/etc/rc.local** and above the *exit 0* command, add the line:
```
echo 6 > /sys/class/backlight/acpi_video0/brightness
```

I did that, but it didn't work.  This is what I got from running the script.

```
 john@kotux:/etc$ sudo ./rc.local
./rc.local: 14: ./rc.local: cannot create /sys/class/backlight/acpi_vide0/brightness: Directory nonexistent

```

---

### Post by pqwoerituytrueiwoq on 2013-05-20
try installing xbacklight and use lightdm to set it
[FONT=courier new]xbacklight -set 50[/FONT]
the 50 is a percentage
```
~$ cat /etc/lightdm/lightdm.conf 
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=xubuntu
greeter-setup-script = sh -c 'xbacklight -set 50'
```

---

### Post by Toz on 2013-05-20
> **epikvision said:**
> I did that, but it didn't work.  This is what I got from running the script.

```
 john@kotux:/etc$ sudo ./rc.local
./rc.local: 14: ./rc.local: cannot create /sys/class/backlight/acpi_vide0/brightness: Directory nonexistent

```

You misspelled acpi_video0. The command should be:
```
echo 6 > /sys/class/backlight/acpi_vide**[COLOR="#FF0000"]o[/COLOR]**0/brightness
```

---

### Post by epikvision on 2013-05-21
> **Toz said:**
> You misspelled acpi_video0. The command should be:
```
echo 6 > /sys/class/backlight/acpi_vide**[COLOR=#FF0000]o[/COLOR]**0/brightness
```

Wow, all it took was a typo... Anyway, now it's all good. I'll consider the lightdm solution too for another machine, but finally, this issue has been conquered.

Before I mark the thread as 'solved,' I would like to know if there is any development happening to allow screen brightness to match that of the current session by startup.

---

### Post by Toz on 2013-05-21
> **epikvision said:**
> Before I mark the thread as 'solved,' I would like to know if there is any development happening to allow screen brightness to match that of the current session by startup.
I was hoping to solve this particular issue by using a kernel parameter. However, none seemed to work for your system. Hence the workaround. You may want to [create a bug report]("https://help.ubuntu.com/community/ReportingBugs") if you want to follow up with a proper solution.

---

