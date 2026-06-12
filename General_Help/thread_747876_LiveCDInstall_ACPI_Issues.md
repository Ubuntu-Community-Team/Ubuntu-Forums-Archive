---
title: "LiveCD/Install ACPI Issues"
date: 2008-04-07
forum: General Help
---

### Post by incubii on 2008-04-07
I was going to post this in the Hardy forum but i tested with Fiesty and Gutsy and found the same issue.

To summarize the issue, whether i boot Ubuntu from the LiveCD or try to boot an installed system from the HDD, it always gets stuck at "Starting ACPI".

If i run the system in "single user" mode it boots to the console fine.
If i run the system with "acpi=off" it boot up fine but then i have no USB at all. I have tried all the ACPI options i found on an ubuntu wiki page to no avail.

I updated the system last night to the latest while i was in single user mode and that went fine. I dont quite understand what is going on.

I cant turn ACPI off in the BIOS it wont let me select that option.

Why is it that single user mode doesnt hang on ACPI and allows me to use USB but the other init levels do not.

I am using a AMD FX-62 with 2GB RAM on an ASUS M2N-SLI Deluxe board with inbuilt wifi. It has the latest BIOS installed which fixed instability issues i had a year ago.

Im tempted to try Fedora 8 to see if it has issues but i would rather solve the problem or at least know how to work around it.

What other information can i provide to help me diagnose this issue?

---

### Post by incubii on 2008-04-07
Well as it turns out there is a new bios i can update too. So i will be trying it out first and update with my progress. :)

 	
Version 1802 - 2008/03/06
Description - M2N32-SLI Deluxe BIOS 1802
 * Update to AMD AGESA 3.1.6.0 code.
 * Disable DDR2 1066 option when AM2 CPU is plugged.
 * Fix that AM2+ L3 cache string will overlap.

---

### Post by incubii on 2008-04-07
I didnt bother with the BIOS update. I reset the BIOS to defaults and then tweaked a few things and Ubuntu booted perfectly. I could update the BIOS if i wanted to as it might improve performance but why wreck a beautiful thing? :)

---

### Post by mltom on 2008-04-07
After I installed Xubuntu 7.10, my HD booted up saying APCI=Force,,,,,,,,,,,,but the system does run ok.

Where would one find a bios update & version name for a old Dell?  

later
tks
tom

---

### Post by incubii on 2008-04-07
Well ive never dealt with dell hardware but generally you should be able to see the version of your BIOS when the machine first boots up. If not i would go into the BIOS setup and it should have a version number on one of its screens there.

As for the BIOS update i would go to dells website and look for something like Software & support or drivers. Probably find something under there. There may be no updates available though for your machine.

Hope that helps :)

---

