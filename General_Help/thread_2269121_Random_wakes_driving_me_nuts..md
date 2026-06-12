---
title: "Random wakes driving me nuts."
date: 2015-03-13
forum: General Help
---

### Post by malch2 on 2015-03-13
I have a new Broadwell Intel NUC (NUC5i5RYH) running Lubuntu 15.04 Beta (the Broadwell and HD6000 graphics seem to require the latest kernel and drivers so hence the Beta).

I don't need or want hibernate or suspend. But I do want a remote wake from S5:

1. Via Wake-on-LAN and

2. Via an IR Remote signalling an IR receiver (FLIRC) connected to a front panel USB port.

And the good part is... all of this works.

Unfortunately, something else also causes the system to wake from S5 at random times -- typically 1-4 hours after shutdown.

I really need the equivalent of a Windows "powercfg -lastwake"!

I have searched through dmesg/syslog et al but can find absolutely no clue there.

In /proc/acpi/wakeup there are just 3 devices enabled: GLAN EHC1 XHC.

So I tried disabling them with the following in /etc/rc.local:

```

for device in GLAN EHC1 XHC
   do
     if grep -q "$device.*enabled" /proc/acpi/wakeup
   then
     echo $device > /proc/acpi/wakeup
   fi
done

```

With this in place, the system has twice gone >12 hours without any random wakes. To my surprise it doesn't (immediately) disable remote wakes from WOL or my IR remote. However, on the second run, both appeared to be disabled after 18 hours. That didn't make any sense.

Any suggestions on how to diagnose what's really going one here?

---

### Post by tgalati4 on 2015-03-13
Install *acpitool* and make a list of what parts of the bus remain powered during sleep.

```
sudo apt-get install acpitool
acpitool -w
```

Understand that smallish computers with embedded type Use Cases do not behave the same way as their Laptop/Desktop peers.  Similar problems can be found with the RaspberryPi (ARM CPU) in trying to put parts of the bus to sleep and get them to wake consistently.

---

### Post by malch2 on 2015-03-13
> **tgalati4 said:**
> Install *acpitool* and make a list of what parts of the bus remain powered during sleep.

```
sudo apt-get install acpitool
acpitool -w
```

Understand that smallish computers with embedded type Use Cases do not behave the same way as their Laptop/Desktop peers.  Similar problems can be found with the RaspberryPi (ARM CPU) in trying to put parts of the bus to sleep and get them to wake consistently.

Thanks for that. Unfortunately, acpitool -w doesn't tell me anything more than cat /proc/acpi/wakeup.

As mentioned previously, GLAN, XHC and ECH1 are the only devices enabled. I don't think this is a WOL issue so there's fair chances it's USB related.

I have since found this patch which was designed to fix some spurious wakes with Haswell and Lynx Point controllers:

[https://lists.ubuntu.com/archives/kernel-team/2013-October/034013.html](https://lists.ubuntu.com/archives/kernel-team/2013-October/034013.html)

However, the Broadwell NUCs have Wildcat Point controllers and perhaps the fix needs extending for those devices?

---

### Post by tgalati4 on 2015-03-13
Well, what I wanted to see was the disabled devices.  Try turning them on with the -W switch and see if the behavior changes.  This would be a work-around until a proper patch has been tested and incorporated into the kernel.

By keeping other parts of the bus powered during sleep, it reduces the chance of spurious signals which can trigger wakes.  It's counter-intuitive, but often works.  Yes it uses a little more power during sleep, but the trade-off is leaving it on all the time.

---

### Post by malch2 on 2015-03-13
> **tgalati4 said:**
> 
By keeping other parts of the bus powered during sleep, it reduces the chance of spurious signals which can trigger wakes.  It's counter-intuitive, but often works. 

Yep, definitely counter-intuitive :-)

But I get it, and I'll certainly give this a shot. Unfortunately, given the slow and spurious nature of the problem, it can take a day or two to test just one variable with any degree of certainty.

Nevertheless, I really appreciate the input and I will try it. Thank you!

---

### Post by tgalati4 on 2015-03-13
Yes, it is a trial and error process.  Turn everything on and see if it stays asleep.  In my WoL scripts, I send the magic packet 3 times with a 2-second delay between each, because my servers just like to sleep and stay groggy.

If you get spurious wakeups with all parts of the bus powered during S3 or S5 sleep, then you have to wait for a kernel update, or compile your own kernel and apply the patch yourself.  Nothing gives you the satisfaction of rolling your own fix in 3 hours.

On the RaspberryPi, Broadcom (the chip maker) had to issue several firmware updates to deal with issues that we take for granted (as being fixed and stable) in the X86 world.  I expect a similar fix-it cycle will happen with the NUC's.

If it stays asleep for 3 days straight and then wakes up properly with a WoL poke, then shut off (disable) one device and repeat for another 3 days. After a while you will know what needs to stay lit up and what can really sleep during sleep.  The part of the bus that powers the network card usually needs power during sleep.  No blinky, no wakey.

---

### Post by malch2 on 2015-03-13
> **tgalati4 said:**
> Yes, it is a trial and error process.  Turn everything on and see if it stays asleep. 

That will definitely be my next step. However, right now, simply disabling XHC in /proc/acpi/wakeup is looking good. So maybe that XHCI_SPURIOUS_WAKEUP really is at play. I'll run with this one a little longer to see if it holds up.

You're right: it might be fun to try hacking the kernel to apply that fix when it finds a Broadwell/Wildcat controller but I've spend a ton of time on this already. 

But depending on what else happens this weekend, the temptation might prove overwhelming :-)

Thanks again.

---

### Post by coldraven on 2015-03-14
Could it be stray IR from a different remote? Maybe your cat wants to show you cat food adverts. Put some tape over the sensor and see what happens.

---

### Post by malch2 on 2015-03-18
Well, this continues to drive me nuts.

I have tried adding "acpi.debug_layer=0xffffffff acpi.debug_level=0x2" to the kernel boot but I still can't find any indication in the logs as to what initiated the wake. Not even if I deliberately wake the system with a WOL packet.

I can't imagine I'm going to make a progress with this unless/until I can have the kernel capture and record the event that initiated the wake up. So now the question is how to accomplish that?

Perhaps this is something for the kernel developers? It seems to me that it would be a very helpful feature for other users rather akin to a Windows powercfg -lastwake.

Any suggestions on how to do this or where to direct the question very much appreciated.

---

