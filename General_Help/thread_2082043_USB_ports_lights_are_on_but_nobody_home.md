---
title: "USB ports: lights are on but nobody home"
date: 2012-11-08
forum: General Help
---

### Post by nthnwdhs on 2012-11-08
I need a list of commands and remedies to test my USB ports to see what is wrong with them.

I have a Dell 8300 dimension desktop which I had at once stage dual boot with windows and Debian where the ports worked fine.

Then I left the computer with someone and when I came back I needed to re-install the operating systems but since I have not had USB working since.

I have tried XP, Open Suse, Debian and Ubuntu (various versions) but no luck.  I think it is more involved than manually mounting them (but not totally ruled out).

I have also at one stage opened the tower to clean out the cd rom (so it could be possible that I knocked a few wires).

When I put in a flash drive, its light goes on  (so there is power) but it doesn't flash.

I suspect I need to flash the BIOS but I just want to cover everything else first because I am more than likely to ruin the PC entirely doing that.

Here is a dump from lsusb:```
lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```Any help is appreciated.

---

### Post by Wim Sturkenboom on 2012-11-08
Run _sudo dmesg -c_. Next insert the memory stick and post the output of _dmesg_.

The first command simply clears dmesg's ring buffer (after displaying its contents) so you start with a clean slate. The second command is the one that gives the relevant output.

PS
Does your BIOS allow to disable USB ports?

---

### Post by nthnwdhs on 2012-11-08
> **Wim Sturkenboom said:**
> Run _sudo dmesg -c_. Next insert the memory stick and post the output of _dmesg_.
Nothing was output.
> 
Does your BIOS allow to disable USB ports?In the BIOS there is a menu option of "Integrated Devices (Legacy Select Options)" and in that menu you can set "USB Emulation" and "USB Controller".  But both of these were set to "On".

Thanks for the reply, what should I do next?

---

### Post by Wim Sturkenboom on 2012-11-09
If nothing was shown, it was not recognized at all. I'm not sure about BIOS option, maybe somebody else.

With my limited knowledge regarding the subject, I would play with the two options
off / off
off / on
on / off
on / on
And see if you can get it working that way.

As this is not specific to one OS, it must be hardware / bios related.

---

### Post by nthnwdhs on 2012-11-09
No luck.

So does it mean that the driver cannot be the cause since dmesg had not output?

---

### Post by Wim Sturkenboom on 2012-11-09
> **nthnwdhs said:**
> So does it mean that the driver cannot be the cause since dmesg had not output?i can not say, but seen the fact that no OS detects your stuff, it must be the computer itself.

---

### Post by varunendra on 2012-11-11
> **nthnwdhs said:**
> I have also at one stage opened the tower to clean out the cd rom (so it could be possible that I knocked a few wires).Is the situation same with the back ports? They are directly sold on the motherboard, so no wire factor.

> **nthnwdhs said:**
> I suspect I need to flash the BIOSAssuming it's a corrupt setting rather than a corrupt BIOS, did you try a BIOS reset? Apart from the model dependent jumper method, a common method is to just pull out the MB battery and leave it for a while (4 minutes to overnight.. as required). Give it a shot since flashing BIOS is a bit risky business.

---

