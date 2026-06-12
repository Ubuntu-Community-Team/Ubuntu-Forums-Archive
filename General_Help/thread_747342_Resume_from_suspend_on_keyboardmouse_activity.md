---
title: "Resume from suspend on keyboard/mouse activity"
date: 2008-04-06
forum: General Help
---

### Post by revane on 2008-04-06
Hi,

On my x86 desktop running Ubuntu 7.10 suspend works for me, but not quite to my liking. I found that I had to hit the power button to resume. I know the hardware supports resume from keyboard/mouse activity as I have Vista 64 (ick!) dual booted and resume works fine there. I've done a fair bit of research already so I'll briefly recap.

I followed along with this thread:
[http://ubuntuforums.org/showthread.php?t=711747](http://ubuntuforums.org/showthread.php?t=711747)

Here's my machine's info:

revane@samus:~$ dmesg | grep Keyboard
[   52.857612] input: LITEON Technology USB Multimedia Keyboard as /class/input/input1
[   52.857640] input: USB HID v1.10 Keyboard [LITEON Technology USB Multimedia Keyboard] on usb-0000:00:1a.2-1

revane@samus:~$ dmesg | grep Mouse
[   52.872614] input: Microsoft Microsoft 5-Button Mouse with IntelliEye(TM) as /class/input/input2
[   52.872663] input: USB HID v1.10 Mouse [Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)] on usb-0000:00:1a.2-2

revane@samus:~$ cat /proc/acpi/wakeup
Device  S-state   Status   Sysfs node
P0P2      S4     disabled  pci:0000:00:01.0
P0P1      S4     disabled  pci:0000:00:1e.0
UAR1      S4     disabled  pnp:00:09
PS2K      S4     disabled  pnp:00:0b
EUSB      S4     disabled  pci:0000:00:1d.7
USBE      S4     disabled  pci:0000:00:1a.7
P0P5      S4     disabled  
P0P6      S4     disabled  
P0P7      S4     disabled  
P0P8      S4     disabled  pci:0000:00:1c.4
P0P9      S4     disabled  pci:0000:00:1c.5
USB0      S4     disabled  pci:0000:00:1d.0
USB1      S4     disabled  pci:0000:00:1d.1
USB2      S4     disabled  pci:0000:00:1d.2
USB3      S4     disabled  
USB4      S4     disabled  pci:0000:00:1a.0
USB5      S4     disabled  pci:0000:00:1a.1
USB6      S4     disabled   pci:0000:00:1a.2
P0P4      S4     disabled  pci:0000:00:1c.0

So you'll see that my mouse and keyboard are on 1a.2, which is USB6. So I did:
revane@samus:~$ sudo -s
root@samus:~# sudo echo USB6 > /proc/acpi/wakeup

And /proc/acpi/wakeup was updated accordingly. I tried to suspend and the OS began going through the motions. However I was immediately prompted with a login prompt as if a resume had just happened. I got a popup warning that suspend had failed.

I also tried editting /etc/default/acpi-support by adding ehci_hdc to the MODULES list (those that get unloaded before suspend and reloaded upon resume) with no effect.

Attached is the dmesg log for all relevant messages. What is very suspicious to me is at timestamp 11200.920000 (the ACPI Exception). Also, you'll notice the message:

[11200.936000] Could not suspend device 0000:03:00.1: error -22

I looked through dmesg to find this info on device 00.1:

[   49.081585] PCI: Enabling device 0000:03:00.1 (0000 -> 0001)
[   49.081592] ACPI: PCI Interrupt 0000:03:00.1[B] -> GSI 17 (level, low) -> IRQ 17
[   49.081625] PCI: Setting latency timer of device 0000:03:00.1 to 64

I'm afraid when it comes to Linux inner workings I'm a bit of a newb. Could somebody shine some light on this so I can fix the problem?

Edwin V

---

### Post by revane on 2008-04-09
No advanced users out there have any advice to offer or ideas as to what the problem is?

---

### Post by trojanfoe on 2008-05-27
Are you suspending to memory (S3) or hibernating to disk (S4)?  If it's S3 then I think you have the same problem as me where the s-state of /proc/acpi/wakeup is showing the buses as S4 when you want them to be S3.  I have only just started investigating this problem, but suspect the s-state is affected by the BIOS settings given I cannot see a way to change them via Linux. (I am testing a suspend alarm wakeup at the moment on the machine so don't want to disturb it until tonight).

Cheers,
Andy

---

