---
title: "Function keys don't work, but brightness slider does. Eh?"
date: 2013-05-14
forum: General Help
---

### Post by Roasted on 2013-05-14
I'm on a Lenovo E430 laptop with 13.04 installed. When I adjust the function brightness keys, it will decrease my brightness with one tap to 1% brightness. If I try to bump the brightness up it does nothing at all. On the flip side, if I go into system settings and adjust the brightness slider, it works fine. What's the difference? Clearly these two things aren't tied together since one works and the other does not... is there a way to tie in the brightness slider in system settings to the function keys instead?

---

### Post by Toz on 2013-05-14
Does using the **acpi_osi=\"!Windows 2012\"** kernel parameter to help? 

To set up your system to use this parameter:
1. Edit /etc/default/grub:
```
gksu gedit /etc/default/grub
```

2. Change the line that reads:
> GRUB_CMDLINE_LINUX=""
...to read:
```
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""
```

3. Save the file.

4. Run:
```
sudo update-grub
```

5. Reboot.

---

### Post by Roasted on 2013-05-15
Wow. That worked. It's flawless now. Thank you so much! 

For the sake of me understanding, as well as the fact I want to update the bug report I submitted with as many details as possible, can you tell me what exactly that did? I find it insanely strange that something entitled Windows 2012 was what fixed it for me... I'd really appreciate it. Thanks again!

---

### Post by Toz on 2013-05-15
As I understand it, Windows 8 changed the way it addresses brightness (See: [http://msdn.microsoft.com/en-us/library/windows/hardware/jj159305.aspx]("http://msdn.microsoft.com/en-us/library/windows/hardware/jj159305.aspx")). Laptop manufacturers have updated their acpi tables to accomodate (I'm guessing for newer Windows 8-capable devices - involving the second bit of the ACPI _DOS method). This parameter ("!Windows 2012") tells the bios that you are not Windows 8 (Windows 2012), so a different set of acpi tables are loaded. This different set of tables then allows the bios to control the brightness again.

---

### Post by Firstl4rs on 2013-06-30
I had a similar problem on my ProBook 6570b: Brightness OSD appeared but brightness didn't change. Brightness slider in settings didn't work either. Solution posted above worked flawlessly for me! Thanks a lot!

---

### Post by Toz on 2013-06-30
> **Firstl4rs said:**
> I had a similar problem on my ProBook 6570b: Brightness OSD appeared but brightness didn't change. Brightness slider in settings didn't work either. Solution posted above worked flawlessly for me! Thanks a lot!

Glad to hear. And welcome to the forums.

---

### Post by dovah on 2013-06-30
> **Toz said:**
> Does using the **acpi_osi=\"!Windows 2012\"** kernel parameter to help? 

To set up your system to use this parameter:
1. Edit /etc/default/grub:
```
gksu gedit /etc/default/grub
```

2. Change the line that reads:

...to read:
```
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""
```

3. Save the file.

4. Run:
```
sudo update-grub
```

5. Reboot.

Hello! I've got quite a similar problem using an AsusX501A, with Xubuntu 13.04 running on it! Normally brightness values decrease while typing fn+f5 and increase by typing fn+f6 but now nothing seems to work anymore, i have to decrease brightness by using xrandr at every reboot!
I tried the path you suggested by typing in a terminal window ```
gksudo gedit /etc/default/grub
``` so i modified the file like this: ```
# If you change this file, run 'update-grub' afterwards to update# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT= "splash quiet acpi_osi="
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\"


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
```

but, by updating in terminal, i got back this error: ```
Searching for GRUB installation directory ... found: /boot/grub
/etc/default/grub: line 11: splash quiet acpi_osi=: command not found
``` ...

can you please understand the problem and help me somehow? this brightness is killing me :(

---

### Post by Toz on 2013-06-30
Hello and welcome to the forums.

First, you're missing a quote on the GRUB_CMDLINE_LINUX line. It should read:
```
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\"**[COLOR="#FF0000"]"[/COLOR]**
```

Secondly, I would recommend removing the acpi_osi= parameter, as it will be redundant. That line should read:
```
GRUB_CMDLINE_LINUX_DEFAULT= "splash quiet"
```

And finally, what kind of video card(s) do you have? This command will help identify them:
```
sudo lspci -vnn | grep -A12 VGA
```

---

### Post by dovah on 2013-06-30
The answer to the command you asked me is: 
```
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0106] (rev 09) (prog-if 00 [VGA controller])    Subsystem: ASUSTeK Computer Inc. Device [1043:14f7]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f7800000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915


00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04) (prog-if 30 [XHCI])
```

i'm fixing the syntax problem, let's see what's up *thank you* 

edit: 
by editing this way: ```
# If you change this file, run 'update-grub' afterwards to update# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT= "splash quiet"
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""


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

and then updating, the answer is: 

```
Searching for GRUB installation directory ... found: /boot/grub/etc/default/grub: line 11: splash quiet: command not found
```

---

### Post by dovah on 2013-07-16
That's ok, I reinstalled the system and edit ONLY the line you suggested, this way: ```
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\"[COLOR=#FF0000]"[/COLOR]
```
but, in ```
GRUB_CMDLINE_LINUX_DEFAULT= "splash quiet"
``` i edited this way: ```
GRUB_CMDLINE_LINUX_DEFAULT= ""
```

Everything's working fine!! ^^

Huge thanks!

---

