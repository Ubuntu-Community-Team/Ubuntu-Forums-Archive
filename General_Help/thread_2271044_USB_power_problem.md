---
title: "USB power problem"
date: 2015-03-27
forum: General Help
---

### Post by georgesgiralt on 2015-03-27
Hello !
I own a brand new Lenovo laptop (E540, 20C600JHFR). As I suffer from my right wrist, !I use an ergonomic mouse (Evoluent) so always have something plugged on USB buses.
This laptop maintain power on the plugged USB ports when set to sleep mode. If this is not annoying when the laptop is fed with the mains, it is terrible when on battery because it drains it very fast.
I've checked all BIOS settings but to no avail. 
So I wonder if something is possible into Ubuntu to correct this stupid behavior.
I use Ubuntu 14.04 LTS.
All the help you can give will not go unnoticed and I thank you in advance for it.
Have a bright day !

---

### Post by dino99 on 2015-03-27
as that laptop is new, then complaint/report on the make forum, and browse about that model's issues; maybe you are not alone having that problem.
of course when it use the battery, the solution is to unplug the unused device(s) if possible.
some laptop have a really too light battery (dont know about yours)

---

### Post by tgalati4 on 2015-03-27
What parts of the bus remain powered when your laptop is put to sleep?

```
sudo apt-get install acpitool
acpitool -w
```

---

### Post by DuckHook on 2015-03-28
I believe that the default behaviour for all OS/MOBO combos is to keep USB powered on while in sleep mode. This is so that USB HDDs don't suddenly lose power with cached but unwritten data and thus corrupt your data and even your whole file structure. Since this is an extremely serious danger, I'm not aware of any workaround that disables it; nor, perhaps, ought there to be one.

Aside from pulling your USB peripheral before putting your laptop to sleep, try suspending your laptop instead. I haven't tried this myself, but this should properly flush your cache, spin down any connected USB HDD and power everything off. If suspend doesn't do the trick, you may have to reactivate hibernation on Ubuntu, which is a much more involved process.

---

### Post by georgesgiralt on 2015-03-28
Tgalati4, here are the results :
/code
 acpitool -w
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. LID	  S3	*enabled 
  2. IGBE	  S4	*disabled
  3. EXP4	  S4	*disabled  pci:0000:00:1c.3
  4. EXP5	  S4	*disabled  pci:0000:00:1c.4
  5. XHCI	  S3	*enabled   pci:0000:00:14.0
  6. EHC1	  S3	*enabled   pci:0000:00:1d.0
  7. EHC2	  S3	*enabled   pci:0000:00:1a.0
  8. HDEF	  S4	*disabled  pci:0000:00:1b.0
~$ 
/code
I do not know what's the meaning of that, though...

---

### Post by tgalati4 on 2015-03-28
Well, you can now shut off parts one-by-one.  Be mindful of DuckHook's warnings, but give this a try:

Let's shut off port #7:

```
sudo acpitool -W 7
acpitool -w
```

What is the behavior of your eronomic mouse now?  If you have a problem, repeat the command to toggle the device back to "enabled", which means leave power to it during S3 level sleep.

If that doesn't fix the problem, repeat with 6, then 5.

For output, use the "quote" tags  [  quote  ] followed by [   /   quote  ]-- but take out the spaces.

---

### Post by georgesgiralt on 2015-03-28
Hello 
7 did not do the trick.
Here is my lsusb output.. 
```

georges@boudiou:~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 8087:07dc Intel Corp. 
Bus 003 Device 002: ID 1a7c:0068 Evoluent VerticalMouse 3
Bus 003 Device 005: ID 5986:0397 Acer, Inc 
Bus 003 Device 007: ID 138a:0011 Validity Sensors, Inc. VFS5011 Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```
How could I tell which number to toggle to switch the Evoluent mouse off ? 
And when known how could I do to make the trick automatic when closing the lid ? 
Anyway, thanks for your help !

---

### Post by DuckHook on 2015-03-28
Thanks, tgalati4. All these years playing with Linux and I did not know of the existence of acpitools. This thread has been very educational if only for that.

@georgesgiralt

Please follow tgalati4's instructions:> **tgalati4 said:**
> If you have a problem, repeat the command to toggle the device back to "enabled", which means leave power to it during S3 level sleep.

If that doesn't fix the problem, repeat with 6, then 5....it is ***very*** important to note that you must use a capital "W" to toggle. Case is critical in Linux. Lowercase "w" only lists devices with wakeup capabilities. Uppercase "W" enables/disables. You really should have a look at acpitool's man page to get more familiar with it before proceeding further.

As previously suggested, have you tried suspending instead? When sleep is not meant to shut down peripherals, but suspend is, why would you keep trying to force-fit a square peg into a round hole?

---

### Post by georgesgiralt on 2015-03-28
No I did not. Why ? Because my menu shows "sleep" "log off" and "power down". No suspend.

---

### Post by tgalati4 on 2015-03-28
My Acer laptop has the USB ports clearly labeled:

> tgalati4@Mint17 /etc/default $ acpitool -w
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. LID0	  S3	*enabled 
  2. SLPB	  S3	*enabled 
  3. HDEF	  S3	*disabled  pci:0000:00:1b.0
  4. PXSX	  S5	*enabled   pci:0000:02:00.0
  5. USB1	  S3	*enabled   pci:0000:00:1d.0
  6. USB2	  S3	*enabled   pci:0000:00:1d.1
  7. USB3	  S3	*enabled   pci:0000:00:1d.2
  8. EHC1	  S3	*enabled   pci:0000:00:1d.7


Yours does not, so you have to try things one at a time to see if it makes a difference.  My USB ports can be shut off when my laptop is in S3 sleep state (technically suspend-to-RAM).  S4 sleep is hibernation--RAM is written to the hard disk (make sure your swap file is bigger than RAM) and the machine is completely off.

With your laptop, you don't have much choice.  Device #1 is the lid switch.  If you disable that, then your laptop won't wake up if you open the lid; you will have to use the power button instead.  That leaves Device 5 and 6, so try those.

---

### Post by georgesgiralt on 2015-03-29
So I tried all numbers in the list except for the lid switch.
No joy. 
As, at first I thought it was hardware related, I asked for warranty and they exchanged my main board. Of course it  does not change anything .... 
So it seems I'm left with unplugging the mouse when turning the machine to sleep. 
P.S. my swap space is 6.1 GB (windows driver space reclaimed... to good use) and the RAM is 4GB so I wonder why I can't put it in hibernation mode ?

---

### Post by DuckHook on 2015-03-29
> **georgesgiralt said:**
> No I did not. Why ? Because my menu shows "sleep" "log off" and "power down". No suspend.> **georgesgiralt said:**
> I wonder why I can't put it in hibernation mode ?There is a middle state between sleep and hibernate that is available on some motherboards but apparently not on yours. It acts just like sleep but with a few extra steps: it purges your cache, spins down HDDs and puts all peripherals capable of doing so into suspend state before pushing the system to RAM. This ensures no corrupted files in external disk drives but *it does not cut power to the USB ports*. In the case of your peripheral, I doubt that it has the circuitry to suspend.

So, on my system, if I simply close the lid, the system goes to sleep&#8213;meaning the display is powered down and the HDD is spun down, but the system is still active with CPU ticking away, eating up all that power. The sleep option will not change the state of any device plugged into the USB port.

If I actually select "suspend", then in addition to the steps in sleep, the CPU state is shoved into RAM, the CPU goes into hibernation and it eats very little power. It also sends a different signal to the USB port instructing them to "suspend" as well. Intelligent devices have the circuitry to go to sleep. Dumb devices will not. But on most MOBOs power continues to be fed to the USB port in the interest of data safety.

Hibernate is the option that writes the whole system state to your HDD and then completely powers off the physical machine. It is the only option that will work in your case. It is a known data corruption danger in Linux and is therefore unavailable in Ubuntu by default. You can turn it back on manually, but consider yourself warned. Instructions [here]("http://askubuntu.com/questions/94754/how-to-enable-hibernation").

---

### Post by matt_symes on 2015-03-29
Hi

I think you need to unbind the driver that controls the internal hub the mouse is connected to via the USB port on the PC.

If i remember correctly, this will power down that hub and any devices connected to it (in your case the mouse).

You can use 

```
lsusb -t
```

to find the hub the mouse is connected to and create script files to unbind the driver when the PC is suspended and rebind when resumed.

In the first instance post the output if the lsusb command above.

Kind regards

---

### Post by georgesgiralt on 2015-03-29
Here we are :
```
georges@boudiou:~$ lsusb -t
/:  Bus 04.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/6p, 5000M
/:  Bus 03.Port 1: Dev 1, Class=root_hub, Driver=xhci_hcd/14p, 480M
    |__ Port 2: Dev 2, If 0, Class=Human Interface Device, Driver=usbhid, 1.5M
    |__ Port 7: Dev 3, If 0, Class=Wireless, Driver=btusb, 12M
    |__ Port 7: Dev 3, If 1, Class=Wireless, Driver=btusb, 12M
    |__ Port 11: Dev 4, If 0, Class=Vendor Specific Class, Driver=, 12M
    |__ Port 12: Dev 5, If 0, Class=Video, Driver=uvcvideo, 480M
    |__ Port 12: Dev 5, If 1, Class=Video, Driver=uvcvideo, 480M
/:  Bus 02.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/3p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/8p, 480M
/:  Bus 01.Port 1: Dev 1, Class=root_hub, Driver=ehci-pci/3p, 480M
    |__ Port 1: Dev 2, If 0, Class=Hub, Driver=hub/6p, 480M
georges@boudiou:~$ 
``` 
Could you please help me learn how to unbind the driver for the relevant USB hub ?
Thanks.
P.S. I'll give a look at the hibernation... I used it a log time ago in Windows and in Linux at the same time. It was fun when powering back the machine and when lilo popped up ;-)

---

### Post by tgalati4 on 2015-03-29
You could add *evdev* to the list inside of this file:

```
cat /etc/default/acpi-support
```

Basically, you remove the module just before suspend and reload the module coming out of suspend.  This may or may not fix the power problem, but it's worth a try.

---

### Post by DuckHook on 2015-03-29
All good suggestions, but it's an *awful* lot of trouble to go through just to turn one peripheral off. I would either just physically yank the thing or reactivate hibernation and be done with it. It's your call if this sort of obscurity and messing around in the guts of your OS is worth it.

---

