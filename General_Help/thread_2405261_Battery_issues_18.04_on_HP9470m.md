---
title: "Battery issues 18.04 on HP9470m"
date: 2018-11-03
forum: General Help
---

### Post by chris-1024 on 2018-11-03
Hi,

Ubuntu first-timer, please be gentle.

I successfully installed 18.04LTS Desktop on HP 9470m laptop (old Win-7 SSD removed, new 500GB Crucial added with a single aligned partition for Ubuntu, no dual boot).
Almost everything went blissfully well, and I'm now going thru my half-dozen ToDo items to remove that qualifying "Almost".

The biggest annoyance that I have not found a fix for is the laptop battery:

Machine has been on mains power since beginning the installation (around 120 hours)

Battery gauge says "estimating"

Power Statistics shows:
Time to full        0 seconds
Time to empty   0 seconds
...so it is completely lost.

Without mains power the machine drops dead immediately.
This is relatively inconvenient on a laptop :(

Any suggestions for diagnostic steps or fixes?

Chris

---

### Post by him610 on 2018-11-03
If your HP 9470m is still on its original battery, there is not much you can do except replace the battery( ~$50 at Amazon - [https://www.amazon.com/HWG-BT04XL-Compatible-687945-001-HSTNN-IB3Z/dp/B0777BLJ7Q/ref=sr_1_1_sspa?ie=UTF8&qid=1541282554&sr=8-1-spons&keywords=hp+9470m+battery&psc=1]("https://www.amazon.com/HWG-BT04XL-Compatible-687945-001-HSTNN-IB3Z/dp/B0777BLJ7Q/ref=sr_1_1_sspa?ie=UTF8&qid=1541282554&sr=8-1-spons&keywords=hp+9470m+battery&psc=1")),
or you could just continue using it connected to AC Power. I have two older laptops that have lost their portability due to old batteries. I have another one that is just about due for a battery replacement. It's a tradeoff whether to buy a new battery or put that money into a newer laptop. Laptop batteries begin deteriorating the day of manufacture, and seldom last more than three or four years.

A laptop powered from mains power is still more portable than a desktop + monitor + keyboard & mouse.

---

### Post by Autodave on 2018-11-03
Was the battery working right before you switched to Ubuntu?  If so, here is a quick thing you can try:

Shut down normally. Remove power cord and every other cord. Remove battery.  Let it set like that for 10 minutes. Reinstall battery and power cord. Do NOT turn laptop on.  Just leave it sit like that for at least 1/2 hour to 45 minutes.  Now power up and see what indicator says.

---

### Post by chris-1024 on 2018-11-04
Thanks for the replies.
Some history:
I have two of these 9470's.
A couple of years ago they were on the same network.
My niece visited, connected to the guest network, and my mailbox started filling up with full logs from my security gateway: her machine turned out to have a massive collection of malware!
Both 9470's were switched off after a minute or so and haven't run since.
Guest and private networks were supposedly completely segregated, but maybe something in her malware collection was smart enough to find a way through ...I did not want to risk it so bought a couple of Mac-Airs a few days later.

@him610:
My son will move the second 9470 to Ubuntu today -- it was always going to be permanently tethered to the mains at his girlfriend's apartment, so even if it also has battery issues, it still remains a very useful machine.

The first 9470 was going to be used by me (in an attempt to learn something about Linux). I move around when I'm learning stuff and need at least some battery power ...will likely trash the 9470 if I can't get it going and move the 500GB SSD into some other minimum spec machine.

@Autodave:
Two years ago the battery was working perfectly ...the machine has not run since then.
It costs me absolutely nothing to try your idea, so I'll give it a go when I've posted this.

...but I'm not too optimistic. I've been digging around in the logs this morning and discovered that this occurs on every boot:

Nov  1 10:11:29 jacala2 kernel: [    4.203543] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042F conflicts with OpRegion 0x0000000000000400-0x000000000000047F (\PMIO) (20170831/utaddress-247)
Nov  1 10:11:29 jacala2 kernel: [    4.203550] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Nov  1 10:11:29 jacala2 kernel: [    4.203554] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
Nov  1 10:11:29 jacala2 kernel: [    4.203558] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Nov  1 10:11:29 jacala2 kernel: [    4.203559] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
Nov  1 10:11:29 jacala2 kernel: [    4.203563] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
Nov  1 10:11:29 jacala2 kernel: [    4.203564] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052F conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20170831/utaddress-247)
Nov  1 10:11:29 jacala2 kernel: [    4.203568] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver

 
Hmmmmm -- that doesn't look promising. 
No APCI almost certainly means no power management!

Chris

---

### Post by chris-1024 on 2018-11-04
@Autodave

Tried your idea (and when that didn't help, tried a dozen variations on the same theme smeared all over the internet). 
No change.
During the process(es), when the battery goes in the charge light is initially (blue to colour-blind me, but probably meant to be) white, and then trips over to 2 Hz flashing red: not a joyful sign :(

I'm mostly out-of-action for the next two days (grandchildren in the house doesn't help concentration).

Wednesday I'll flash the BIOS and see what that brings to the party.
Current BIOS is F44 (...targeting the original Win7pro). I see F46 (targeting Linux {suse & redflag, but ho hum} ) on hp's site. 
I'm reluctant to go straight to the latest BIOS (Linux or Win) since there is no way back.
 
 Worst case is I brick the machine... and go buy a minimum-spec host for my 500GB SSD and 16GB RAM.

Chris


PS: 
Just before hitting the "post" button, my son reports that the other 9470m installed 10.04 perfectly **AND** works correctly with the battery.
He followed the install script prepared by me and used the boot-able USB-chip I prepared.

PPS:
My charge LED has upped tempo: red flashes at around 4Hz.

PPPS:
Only difference between son's install and mine is that I turned off journal on ext4 partition before the install (installer turned it on again for me, so I deleted the pointless turn-off step from the script my son followed)

---

### Post by Autodave on 2018-11-04
Swap the batteries and see what happens????  Flashing red lights are NEVER a good indicator of anything unless they are on a Christmas tree.  Ask Santa for a new battery if swapping it make the problem go to the other machine.

I have replaced MANY laptop batteries.....some of which were barely a year old.

---

