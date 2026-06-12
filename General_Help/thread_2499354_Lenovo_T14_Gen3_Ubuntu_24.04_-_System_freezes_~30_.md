---
title: "Lenovo T14 Gen3 Ubuntu 24.04 - System freezes ~30 seconds after waking from sleep"
date: 2024-07-23
forum: General Help
---

### Post by s41ted on 2024-07-23
Hi, 

I am looking for assistance. I have installed Ubuntu 24.04 on my Lenovo ThinkPad T14 Gen 3 (AMD Ryzen™ 7 PRO 6850U with Radeon™ Graphics × 16).

Since install, the following problem has occurred:

Whenever I suspend the system (e.g. power off menu > suspend), the system successfully goes into a suspended state. 

When I wake the computer, the computer wakes and presents me with the login screen

I can log into the system, and the mouse and all previously open windows appear to be working, sound is working etc

I CAN'T open any new applications or run any new commands at this time (no error messages, just nothing starting)

Approximately 30 seconds to 1 minute later, the system freezes completely. No error messages, and I can see everything on the screen. But mouse/keyboard input stops, sound stops, and I have to physically hard restart the laptop. 

I have not been able to find a solution to the problem as yet. 

I have updated all the firmware / BIOS to the latest versions, and the issue still persists. 

Any help would be appreciated!!

---

### Post by currentshaft on 2024-07-23
Try this suspend test tool by Intel: [https://github.com/intel/S0ixSelftestTool/blob/main/s0ix-selftest-tool.sh](https://github.com/intel/S0ixSelftestTool/blob/main/s0ix-selftest-tool.sh)

---

### Post by s41ted on 2024-07-25
Does this work for AMD laptops? Are there other intel-branded components in the laptop that the system suspend relies upon? 

I have started running the tool and it is complaining that Intel drivers are not installed/loaded. I am guessing that is because I have an AMD processor?

---

### Post by currentshaft on 2024-07-25
I've used it on AMD ThinkPads successfully to troubleshoot sleep issues.

---

### Post by s41ted on 2024-07-25
Ignore me - I hadn't downloaded the turbostat binary in that repo. 

The script ran - sent the machine into suspend/sleep, got it out of sleep, and the script was doing its thing..... and then the laptop froze! So didn't give me any output.

Any other ideas?

---

### Post by s41ted on 2024-07-25
For what it is worth - 

Downloaded all files from the git repo, ensured the script and turbostat were executable
Ensured intel_pmc_core was loaded (sudo modprobe intel_pmc_core & lsmod | grep intel_pmc_core to validate)
Ran the script with -s flag

Took the system into suspend and out again
Script complaining that files were empty and/or missing, and then before it could finish, system froze. 

Found an output log file in the same path of the script, and at the end of the output file, it says:

> ---Judge PC10, S0ix residency available status---:
Test system does not support S0ix.y substate

---

### Post by currentshaft on 2024-07-25
When the system freezes after resuming from suspend, what happens if you press Control-Alt-F4?

---

### Post by s41ted on 2024-07-25
Unfortunately nothing. 

For what it is worth, when I press the capslock key under normal circumstances, the keyboard light on that key lights on and off everytime I press. When the system is frozen under this condition, that light doesn't go on/off.

However, there is a light on the Esc key call the FnLock (toggles between F keys and the special functions like volume up and down). When in a frozen state, that FnLock light does turn on and off. Everything else is unresponsive.

---

### Post by s41ted on 2024-07-25
Unfortunately, disabling IOMMU didn't help. I also added an option "acpi_sleep=nonvs" to the same configuration variable in the grub config file, and that didn't work either. Both were suggested when I passed the tail of the journalctl into the Anthropic Sonnet LLM for some clues. Unfortunately no luck.

How and where is the best place to submit this as a bug/issue?

---

### Post by currentshaft on 2024-07-25
You could start by posting about this in the Lenovo Ubuntu forum. They have some staff there available to help.

---

### Post by s41ted on 2024-07-25
Thanks! Ill post back here when I learn more.

---

### Post by s41ted on 2024-08-05
For those following along, have raised with Lenovo, and it appears to be a software bug somewhere. Here is the thread: [https://forums.lenovo.com/t5/Ubuntu/Lenovo-T14-Gen3-AMD-with-Ubuntu-24-04-System-freezes-30-seconds-after-waking-from-sleep/m-p/5324170](https://forums.lenovo.com/t5/Ubuntu/Lenovo-T14-Gen3-AMD-with-Ubuntu-24-04-System-freezes-30-seconds-after-waking-from-sleep/m-p/5324170)

As per instructions on that thread, I have created an Ubuntu Bug here also: [https://bugs.launchpad.net/ubuntu/+bug/2076048](https://bugs.launchpad.net/ubuntu/+bug/2076048)

---

### Post by s41ted on 2024-08-06
Hi all, was notified in the ubuntu bug report that this has been resolved in the next kernel version, which is currently in the "-proposed" update sources. 

The fixed kernel version is: 6.8.0-40-generic

I have installed it on my system and it has resolved the issue for me. 

     For the technically challenged like myself who are reading, here is how I installed it:


 sudo nano /etc/apt/sources.list.d/ubuntu.sources
(Add "noble-proposed" to the end of the line "Suites:" under the archive.ubuntu.com URI)
sudo apt update
sudo apt install linux-tools-6.8.0-40-generic
sudo apt install linux-headers-generic=6.8.0-40.40
sudo apt install linux-generic/noble-proposed
 Restart system

---

