---
title: "Cutting Edge HP Omen X with Ubuntu 18.04 Please Fix this Ubuntu (and my Work-Arounds)"
date: 2019-02-13
forum: General Help
---

### Post by markackerman8@gmail.com on 2019-02-13
Apparently FINALLY SOLVED!  Thanks, Ubuntu.
2 1/2 years later and no NVHDA in the kernel as listed below, but now ...
it is in the kernel and working GREAT, and ...

Hibernation (actually "Pause") is working great with Ubuntu and Nvidia.

I love to be able to say it is solved!

Always Trying to Help, Mark
(but seriously 2 1/2 years later .. well better late than never)
and Nvidia has MINIMAL stuttering now (99% buttery smooth) and NO Screen Tearing

But for some kernels, it is still not loading.  For this here is the workaround!

No NVHDA Solution -  Install a Kernel module to toggle audio function.
&#8728; I can confirm that kernel module, posted by 
&#8227; Maik Freudenberg ([https://bugs.freedesktop.org/show_bug.cgi?id=75985#c27](https://bugs.freedesktop.org/show_bug.cgi?id=75985#c27)),
&#8226; Kernel module to toggle audio function
&#8728;  is working fine on my system. Thank you for the fix. The HDMI audio device now works as it should (now detected).
&#8728; The steps I did to enable HDMI audio device:
&#8226; 1. Download and extract the file nvhda.tar.xz.  (from above link)
&#8226; 2. Run these commands in Terminal,  in the location of the extracted folder 
&#8226; ```
$ make
&#8226; $ sudo make install
&#8226; $ echo nvhda | sudo tee -a /etc/initramfs-tools/modules
&#8226; $ echo "options nvhda load_state=1" | sudo tee /etc/modprobe.d/nvhda.conf
&#8226; $ sudo update-initramfs -u 
```
&#8227; 3. Reboot.
#############################################################################
Problems SOLVED! I
&#8728; Hibernate/Suspend - NVHDA Sound doesn't repopulate 
&#8226; However, if I manually disable the audio output output "sudo tee /proc/acpi/nvhda <<< OFF" I'm then able to get it to sleep. I then have to turn it on again on resume with "sudo tee /proc/acpi/nvhda <<< ON
&#8226; ```
$ sudo tee /proc/acpi/nvhda <<< OFF 
```         (before Hibernation/Suspend or Sleep)
&#8226; ```
$ sudo tee /proc/acpi/nvhda <<< ON
```            (After Resume)
&#8226; SOLVED! I
#########################################################################################

&#8226; ACPI  (Advance Configuration and Power Interface)
&#8226; ERROR "acpi int3400 unsupported event" ERRORS .....
&#8227; Edit Grub
&#8226; ```
sudo gedit /etc/default/grub
```
&#8226; add to "grub's ... 
&#8728; GRUB_CMDLINE_LINUX_DEFAULT="quiet splash",       ... acpi=strict to look like
&#8728; GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=strict"

&#8226; and Change GRUB_TIMEOUT=10 see Grub to GRUB_TIMEOUT=2. This will make the Grub load time to 2 seconds.
&#8226; ```
sudo gedit /etc/default/grub
```
&#8226; ```
sudo update-grub2
```
&#8226; ```
sudo update-initramfs -u
``` (Always a good idea)

&#8226; Limit Time Sop Jobs from taking 1 minute 30 seconds to run hundreds of acpi:3400 errors
&#8226; ```
sudo gedit /etc/systemd/system.conf
```
&#8728; DefaultTimeoutStartSec=3s
&#8728; DefaultTimeoutStopSec=3s
&#8226; ```
sudo update-initramfs -u
``` (Always a good idea)

trying to help as ALWAYS, Mark and ....  Ubuntu PLEASE LISTEN!!!!!!!

---

### Post by markackerman8@gmail.com on 2019-02-16
Also Hibernate / Suspend / Hybrid Sleep Not working right in at least 2 ways

1/ For all of them the NVHDA does NOT reload properly if ...IF ... it actually works otherwise.
A sloppy Workaround is ... 

However, if I manually disable the audio output output "sudo tee /proc/acpi/nvhda <<< OFF" I'm then able to get it to sleep. I then have to turn it on again on resume with "sudo tee /proc/acpi/nvhda <<< ON
• ```
$ sudo tee /proc/acpi/nvhda <<< OFF       
```   
(before Hibernation/Suspend or Sleep)
• ```
$ sudo tee /proc/acpi/nvhda <<< ON
```            
(After Resume)
• **SOLVED!**  Sort OF!

2/ Hibernate not giving an option for wake up properly
i.e.) no blinking cursor and if one presses the power button of the keyboard it DOES a HARD restart not a proper wake up (I know this because my keyboard lights get screwed up 
but 
A solution is to use the terminal command which is  called

sudo pm-hibernate

then and ONLY then does the the keyboard wake up properly from its Sleep

One needs to now press the now completely Unlit power button  (which as least somewhat intuitional )

Tying to help. Mark

---

