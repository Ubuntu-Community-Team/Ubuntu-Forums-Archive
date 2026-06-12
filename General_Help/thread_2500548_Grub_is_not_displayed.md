---
title: "Grub is not displayed"
date: 2024-09-05
forum: General Help
---

### Post by chetinho10 on 2024-09-05
Good morning.


It seems that a Windows update has damaged my Grub with dual boot, I have tried to repair it and reinstall it manually from a LiveCD without success, also, I have tried using Grub-Customizer out of desperation.


Once the computer is turned on, it directly accesses Windows. I have also verified that secure boot was disabled (I did not have it enabled in the BIOS).


I have also tried using Boot-Repair without success.


What else can I do?


Thanks in advance.


Greetings

---

### Post by Rubi1200 on 2024-09-05
Don't use Grub Customizer. It causes more problems than it fixes.

Run the boot repair script from the live medium and post the _pastebin_ link for the _summary report_ here.

Hopefully we can then analyze the results and help you solve this.

---

### Post by chetinho10 on 2024-09-05
Good afternoon  I have run Boot-Repair and attached the requested link, I  have also taken a screenshot that I also attached showing that  Boot-Repair detects /boot.  When I installed Ubuntu I put the Boot in  another partition.  Thank you very much.  Regards.

[https://paste.ubuntu.com/p/r9t5hKzwZV/](https://paste.ubuntu.com/p/r9t5hKzwZV/)

---

### Post by tea for one on 2024-09-05
> **chetinho10 said:**
> Once the computer is turned on, it directly accesses Windows. I have also verified that secure boot was disabled (I did not have it enabled in the BIOS).

In your UEFI settings, is Windows the priority boot option?

---

### Post by chetinho10 on 2024-09-05
Good afternoon.

No, Ubuntu should be the first boot option.

Greetings.

---

### Post by tea for one on 2024-09-05
Do you have two boot options in UEFI boot menu?

---

### Post by tea for one on 2024-09-05
> **chetinho10 said:**
> 
It seems that a Windows update has damaged my Grub with dual boot
Windows update may also have enabled:-
Hibernation
Fast start up (Windows setting)
Fastboot (UEFI setting)

Can you double check these?

---

### Post by yancek on 2024-09-05
Line 200 of your boot repair output shows an Ubuntu entry so the simplest thing to try is to go into the BIOS and set that entry to first boot priority.  You could also do it from the live Ubuntu using the method described at the link below.  Doing it in the BIOS would be best. Reinstalling Grub won't help in your situation.

[https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples](https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples)

---

### Post by chetinho10 on 2024-09-05
Hello
I had Ubuntu, Windows and UEFI Settings.

Until yesterday everything was going well, I loaded Windows and when I restarted the grub no longer appeared.

I have read that a recent Windows update could damage it.

Greetings.

---

### Post by chetinho10 on 2024-09-05
> **tea for one said:**
> Do you have two boot options in UEFI boot menu?

[COLOR=#000000]Hello[/COLOR]
[COLOR=#000000]I had Ubuntu, Windows and UEFI Settings.[/COLOR]

[COLOR=#000000]Until yesterday everything was going well, I loaded Windows and when I restarted the grub no longer appeared.[/COLOR]

[COLOR=#000000]I have read that a recent Windows update could damage it.[/COLOR]

[COLOR=#000000]Greetings.[/COLOR]

---

### Post by chetinho10 on 2024-09-05
> **tea for one said:**
> Windows update may also have enabled:-
Hibernation
Fast start up (Windows setting)
Fastboot (UEFI setting)

Can you double check these?



Hello.
I have verified that both Windows fast startup and hibernation are disabled.


I can't find the FastBoot option (UEFI Settings) from MSI.


Greetings.

---

### Post by chetinho10 on 2024-09-05
> **yancek said:**
> Line 200 of your boot repair output shows an Ubuntu entry so the simplest thing to try is to go into the BIOS and set that entry to first boot priority.  You could also do it from the live Ubuntu using the method described at the link below.  Doing it in the BIOS would be best. Reinstalling Grub won't help in your situation.

[https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples](https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples)


Good afternoon


I have executed the efibootmgr commands, and despite establishing Ubuntu as first it still does not load grub.


Greetings.

---

### Post by tea for one on 2024-09-05
> **chetinho10 said:**
> When I installed Ubuntu I put [COLOR="#0000FF"]the Boot[/COLOR] in  another partition
Can you add some more details?
What is "the Boot"?

---

### Post by chetinho10 on 2024-09-05
Thank you all.


I have already been able to solve it, a BIOS option had been modified.

---

