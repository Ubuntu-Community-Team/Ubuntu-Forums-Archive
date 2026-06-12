---
title: "Editing startup /shutdown scripts"
date: 2007-11-09
forum: General Help
---

### Post by johnnyrevell on 2007-11-09
Hi,
I'm trying to edit my startup/ shutdown scripts so that my feisty installation will shut down a Belkin UPS correctly. The UPS and server are talking to one another fine, but the Belkin UPS has a design problem in that it will not do into soft shutdown until its battery is flat. There is a workaround (see below), but where should I insert the recommended lines?

Regards

John

---Belkin UPS workround (from [http://www.mscs.dal.ca/~selinger/ups/belkin-universal-ups.html#workaround](http://www.mscs.dal.ca/~selinger/ups/belkin-universal-ups.html#workaround))

4. Soft Shutdown Workaround

The main problem with the Belkin Universal UPS is that there appears to be no software way to put the UPS into "soft shutdown" mode. This makes unsupervised recovery from power failures tricky. There is a reliable workaround, as described in this section, but it is awkward. One must conclude that Belkin's engineers do not understand the purpose of a UPS very well, at least as it relates to unsupervised recovery.

To understand the issue, consider what should normally happen to an unsupervised computer (such as a server) during a power failure:

   1. The AC power fails, and the UPS goes on battery mode.
   2. When the battery gets low, the computer enters its normal shutdown sequence.
   3. As the very last step of the shutdown process, the computer signals the UPS to do a "soft shutdown", i.e., to turn its load off and await AC power. This kills the computer's power supply, and thus the computer is turned off.
   4. When the power comes back on, the UPS load comes back on, restoring the computer's power supply, and thus causing the computer to reboot. (Note that there is a BIOS setting by which one can tell the computer to reboot after power loss). 

Moreover, if AC power happens to be restored during step 2, the UPS should still turn its load off briefly in step 3, to allow the computer to reboot.

The problem with the Belkin UPS is that step 3 is not possible. One cannot signal the UPS to do a "soft shutdown". One can only signal it to do a "final shutdown", which means, the UPS stays off even if the power returns. This leaves the entire system in a state where a human needs to press the button on the UPS front panel to restart the system.

There is one way around this problem. Namely, the UPS will enter "soft shutdown" mode when its batteries run out. Thus, it is possible to handle a power failure as follows:

   1. The AC power fails, and the UPS goes on battery mode.
   2. When the battery gets low, the computer enters its normal shutdown sequence.
   3. As the very last step of the shutdown process, we call a special program which does nothing but to monitor the UPS status.
   4. If the AC power comes back on before the batteries run out, our program notices this and causes the computer to reboot.
   5. If the batteries run out before the AC power comes back on, then the UPS shuts off its load, thereby killing the computer's power supply. The UPS is now in "soft shutdown" mode and everything will reboot when the power comes back on. 

The major practical drawback of this solution is that the battery level is guaranteed to be 0% when the system reboots. Thus, if another power failure happens before the batteries are recharged, the system will crash with not enough warning to do an orderly shutdown. We can solve this problem by adding another special purpose program to the startup script, before anything is written to the hard disks, which monitors the UPS and waits for the battery level to reach a minimum amount before allowing the boot process to resume. This ensures that the system is in a safe state, should the power fail again.

I have implemented the required functionality as part of the NUT belkinunv driver. The belkinunv driver can be used as a standalone program by calling it with the "-x wait" option. When called with this option, the driver does not fork into the background, but simply connects to the UPS and waits for AC power to be restored. The intention is that one puts commands such as the following as the last part of the computer's shutdown script:

# NEAR END OF SHUTDOWN SCRIPT:
# if shutdown was caused by UPS, perform Belkin UPS workaround.
if [ -f /etc/killpower ] ; then
    echo "Waiting for AC power, or for UPS batteries to run out..."
    /usr/bin/belkinunv -x wait /dev/ttyS1

    # we get here if the power came back on. Reboot.
    echo "Power is back. Rebooting..."
    reboot
fi

In addition, when called with the "-x wait=level" option, the belkinunv driver waits for the battery charge to reach the specified level. This can be used in a startup script as follows. Put this before any disks are mounted read/write, and before any file system integrity checks, so that the system is in a safe state.

# NEAR BEGINNING OF STARTUP SCRIPT:
# if we are recovering from a power failure, wait for the UPS to
# charge to a comfortable level before writing anything to disk
if [ -f /etc/killpower ] ; then
    echo "Waiting for UPS battery charge to reach 60%..."
    /usr/bin/belkinunv -x wait=60 -x nohang /dev/ttyS1
fi

Here, the "-x nohang" option ensures that the computer will boot properly in case the UPS is no longer attached. There might be many reasons to remove the UPS during a power failure, for instance, you take your computer to a friend's house, or you attach it to a generator, or whatever. Giving the "-x nohang" option ensures that your computer is always bootable.

For a detailed description of the "-x wait" and related options, please see the belkinunv(8) man page.

---

### Post by johnnyrevell on 2007-11-13
any ideas? am truly stuck and don't want to mess up a briiliant OS!

John

---

