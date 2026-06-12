---
title: "Ubuntu 12.04 x64 crashed on me, how to diagnose what went wrong?"
date: 2013-08-31
forum: General Help
---

### Post by CommuneOfLoon on 2013-08-31
As the title says, my computer just crashed on me; details below. I luckily recently backed everything up, so I'm not trying to recover anything, I'd just like to know if and how there is a way to diagnose what happened so I can avoid it when I do a reformat. I've been having issues with this install from the get-go (very slow and laggy, lots of grey-screens, and rather frequent disk checks on startup), so I assume either something went wrong when I last reformatted or I have a hardware issue, neither of which I have enough knowledge to diagnose. 

Details of crash:
I was attempting to install some software via the terminal, and I got an intrusive error message (didn't write it down) while typing, then the terminal froze. I quit out of terminal and reopened it. Again, typing the command, the error message came up, then stopped interrupting my typing, then the terminal was unresponsive as I attempted to add a new repository (ehoover/compholio) and install a program (netflix-desktop). Then terminal and my entire computer completely froze. I manually powered down, and upon powering back up, the initial Ubuntu loading screen came up and did not change. Again, powered down manually, got to the loading page, this time it said 'ubuntu 12.04' and was in a pixellated format. Stayed on this screen for awhile and then went through some code (including 'I/O error, dev/sda'), and then went to a full-screen terminal asking for login, but was not responsive. Again manually powered-down, again went through the same process, but this time ended on a black screen.

Thanks.

---

### Post by CommuneOfLoon on 2013-09-01
Using the recovery mode, I ran dmesg. I don't know what I'm looking for, but there were no obvious error messages. Does this mean I can rule out hardware issues? I've attached a pic of the output (sorry, looks like the forum rotated it).

---

### Post by CommuneOfLoon on 2013-09-01
Another quick note, when the computer initially crashed, I did open up the tower to see if anything was running really hot and it did not seem like anything was.

---

### Post by CommuneOfLoon on 2013-09-01
I just tried dmesg again and realized I was just looking at the very end of the output. Looking at the beginning parts, the following appear multiple times throughout, not necessarily together:


ata1.00: status {DRDY ERR }
ata1.00: error: { UNC }
ata1.00: failed command: READ FPDMA QUEUED
sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
end_request: I/O error, dev sda, sector 1342547976


As well, looking throughout the output, I found these lines that I thought might be helpful, they are not necessarily together in the output (if there is a way to export this output while in recovery mode, I'd be happy to do it):
BIOS was not able to find an aperature
ERST: Table bot found!
GHES: HEST not enabled!
EDAC amd64: DRAM ECC disabled.
EDAC amd64ECC disabled in the BIOS or no ECC capability, module will not load.
Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver.
(Something about ATI) taints kernel.
Disabling lock debugging due to kernel taint
[fglrx] Maximum main memory to use for locked dma buffers: 3294MBytes.
Kernel PAT support not enabled

---

