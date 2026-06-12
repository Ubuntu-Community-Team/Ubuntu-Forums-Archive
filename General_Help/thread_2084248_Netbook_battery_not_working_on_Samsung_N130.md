---
title: "Netbook battery not working on Samsung N130"
date: 2012-11-14
forum: General Help
---

### Post by zenarcadian on 2012-11-14
Hello all,

A problem with an xUbuntu install. Installed last week, works perfectly, until I unplug my netbook. Cuts out. Is there a battery manager or driver I'm missing?

Netbook is a Samsung N130, were really common a few years ago when Argos was putting 'em out a dime a dozen.

---

### Post by varunendra on 2012-11-15
Hi,

Please run the following command in a terminal and show us its result -
```
acpi -i
```

If it returns error like -*"acpi is not installed.."* then install it first by -
```
sudo apt-get install acpi
```

Then retry the first command and post its output here.

---

### Post by zenarcadian on 2012-11-25
Message appearing after ACPI test in Terminal Emulator

[I]Battery 0: Full, 100%
Battery 0: design capacity 4400 mAh, last full capacity 4400 mAh = 100%[/I]

Battery still dies when I unplug. Please advise.

---

### Post by varunendra on 2012-11-25
> **zenarcadian said:**
> Message appearing after ACPI test in Terminal Emulator

[I]Battery 0: Full, 100%
Battery 0: design capacity 4400 mAh, last full capacity 4400 mAh = 100%[/I]

Battery still dies when I unplug. Please advise.

After cutting off if you try to power it on again on battery power, does it turn on again? If not, or even if it does but immediately cuts off again, it means the battery is indeed dead and needs replacement. In some very rare cases it may be a fault in battery charging circuitry in the laptop/netbook, but still a hardware fault if the above symptoms are true.

Acpi or any battery monitoring tool will show it as 100% because it is the usual behaviour of dead batteries to immediately rise to their 'Peak voltage' when charging, and immediately drop when dischrging.

However, if the behaviour is otherwise and the netbook boots (and stays on), then we may have discovered a kernel bug. Please post back what you find.

---

### Post by zenarcadian on 2012-11-27
Big negatory, boss. Doesn't turn on at all. It could be the battery, but!

Never did this before converting to Ubuntu, this happened within a day or two of upgrading. It could be a coincidence, but I'm not sure. Then again my netbook is almost three years old.

---

### Post by varunendra on 2012-11-27
You seem to be already aware of the fact that the role and any effect of the OS comes into scene 'After' the initial booting when BIOS 'POST' is completed and the boot process is handed over to the boot-media. So I'd like to just add a few comments here.

While it is not impossible for an OS to incorrectly detect the battery as 'full' while it is not even being charged, it is a very rare case. The way old batteries usually die is often sudden failure (shorting or immediate power-dropping) of a cell or two when the battery is under pressure and needs current that these 'weakest' cells can no more supply.

So assuming the charging mechanism is working correctly, you may try a few things -

1) pull-out the battery, clean the contacts in both battery and the netbook with a brush and preferably diluted thinner (like nail-polish remover), reseat and see if that was all needed.

2) pull out the battery and leave the netbook 'off' (not connected to AC power) overnight before connecting again. This should take care of BIOS errors if there are any.

3) When the netbook fails to power on, does it give any indication of charging when connected to AC (but not powered on)? If it immediately shows the battery as full (usually '[COLOR="Red"]**red**[/COLOR]' LED means charging and '[COLOR="DarkGreen"]**green**[/COLOR]' is full), the fault can be either in the battery or in charging/backup circuit of the netbook (needs servicing??)! In this case, I'd suggest to test the charging/discharging conditions with a 'test' battery (should be available at repairing shops) before purchasing a new one. Test may be - discharge it by running on battery for 12-15 minutes, then recharge to see if it 'slowly' rises to 'full' again. I'd test it with a full discharge-recharge cycle if can be allowed. :)

By the way, if you use the netbook on battery often, then 'three' years is a quite good time for its life. Typically, [their life]("http://en.community.dell.com/support-forums/laptop/f/3518/t/19389277.aspx") is 300-500 charge/discharge cycles.

.

---

