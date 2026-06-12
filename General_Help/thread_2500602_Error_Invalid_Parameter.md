---
title: "Error Invalid Parameter"
date: 2024-09-06
forum: General Help
---

### Post by chetinho10 on 2024-09-06
Good afternoon


Before loading the grub I get the error that I attached, but after a few seconds, the grub was loaded correctly, how could I fix this error?

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294203&stc=1[/IMG]


Thank you.


Greetings.

---

### Post by tea for one on 2024-09-06
The boot-repair report from your previous thread [https://ubuntuforums.org/showthread.php?t=2500548](https://ubuntuforums.org/showthread.php?t=2500548) contained:-
```
BootOrder: 0007,0008,0005,0006,0003,0004
Boot0001* ubuntu	HD(1,GPT,f6515c66-23a0-45b2-9667-dfbd3539a336,0x800,0x31fff)/File(\EFI\ubuntu\shimx64.efi) File(.[COLOR="#FF0000"]&#18775;&#17486;&#22351;S[/COLOR])
Boot0003* Windows Boot Manager	HD(1,GPT,f6515c66-23a0-45b2-9667-dfbd3539a336,0x800,0x31fff)/File(\EFI\Microsoft\Boot\bootmgfw.efi)0000424f
Boot0004* ubuntu	HD(1,GPT,f6515c66-23a0-45b2-9667-dfbd3539a336,0x800,0x31fff)/File(\EFI\ubuntu\shimx64.efi) File(.)
```
Use the instructions here [https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples](https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples) to remove 0001
Then, if you wish, you can also change the boot order

---

### Post by chetinho10 on 2024-09-07
Good morning 
Sorry for having created two topics, I did it because in the other topic it was because the grub was not visible and it´s now solved.
I already executed the efibootmgr command before opening the topic, I deleted the entry and it,s solved but when I start Windows again I get the error again.

---

### Post by tea for one on 2024-09-07
> **chetinho10 said:**
> Sorry for having created two topics, I did it because in the other topic it was because the grub was not visible and it´s now solved.
No problem
> **chetinho10 said:**
> I already executed the efibootmgr command before opening the topic, I deleted the entry and it,s solved but when I start Windows again I get the error again.
Try and remove the offending text only from the efi entries, where I have marked in red.
May work or may reproduce itself again?
```
BootOrder: 0007,0008,0005,0006,0003,0004
Boot0001* ubuntu	HD(1,GPT,f6515c66-23a0-45b2-9667-dfbd3539a336,0x800,0x31fff)/File(\EFI\ubuntu\shimx64.efi) [COLOR="#FF0000"]File(.&#18775;&#17486;&#22351;S)[/COLOR]
Boot0003* Windows Boot Manager	HD(1,GPT,f6515c66-23a0-45b2-9667-dfbd3539a336,0x800,0x31fff)/File(\EFI\Microsoft\Boot\bootmgfw.efi)0000424f
Boot0004* ubuntu	HD(1,GPT,f6515c66-23a0-45b2-9667-dfbd3539a336,0x800,0x31fff)/File(\EFI\ubuntu\shimx64.efi) [COLOR="#FF0000"]File(.)[/COLOR]

```

---

### Post by chetinho10 on 2024-09-07
[COLOR=#000000]Good night[/COLOR]
[COLOR=#000000]
Now I only had one Ubuntu entry, I deleted it and the other operating system booted.
I have accessed the BIOS and selected Ubuntu to boot as the first option, and when I restarted, the same error appeared again. [/COLOR]I add the output of the efibootmgr command:[COLOR=#000000]
[/COLOR][COLOR=#000000]
[/COLOR]BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001,0003
Boot0001* ubuntu	HD(1,GPT,f6515c66-23a0-45b2-9667-dfbd3539a336,0x800,0x31fff)/File(\EFI\ubuntu\shimx64.efi) File(.&#18775;&#17486;&#22351;S)
Boot0003* Windows Boot Manager	HD(1,GPT,f6515c66-23a0-45b2-9667-dfbd3539a336,0x800,0x31fff)/File(\EFI\Microsoft\Boot\bootmgfw.efi)0000424f
[COLOR=#000000]
Thank you.[/COLOR]
[COLOR=#000000]
[/COLOR]

---

### Post by tea for one on 2024-09-08
> **chetinho10 said:**
> BootCurrent: 0001
Timeout: 1 seconds
BootOrder: 0001,0003
Boot0001* ubuntu	HD(1,GPT,f6515c66-23a0-45b2-9667-dfbd3539a336,0x800,0x31fff)/File(\EFI\ubuntu\shimx64.efi) File(.&#18775;&#17486;&#22351;S)
Boot0003* Windows Boot Manager	HD(1,GPT,f6515c66-23a0-45b2-9667-dfbd3539a336,0x800,0x31fff)/File(\EFI\Microsoft\Boot\bootmgfw.efi)0000424f
Create a new entry for Ubuntu without [COLOR="#FF0000"]File(.&#18775;&#17486;&#22351;S)[/COLOR]
Delete the existing 0001
Power off
Boot into Ubuntu

---

### Post by chetinho10 on 2024-09-15
[COLOR=#000000]Hello
I followed the steps but the same thing happens, as soon as I load Windows 11, I get that error before loading the grub with the list of Operating Systems.

I don't know if I should leave it like that.

Greetings.[/COLOR]

---

### Post by tea for one on 2024-09-15
> **chetinho10 said:**
> I followed the steps but the same thing happens, as soon as I load Windows 11, I get that error before loading the grub with the list of Operating Systems.

Either, Windows is causing this or it is your firmware.
If you remove the offending entry and reboot a few times into Ubuntu, do you see the same error?
Do you have the latest UEFI firmware for your PC?

---

### Post by chetinho10 on 2024-09-15
[COLOR=#000000]Good afternoon

When I delete said entry and start in Ubuntu I don't get the error, but as soon as I log in the first time in Windows after deleting the entry, I get the error every time.

The firmware is up to date.

Greetings.[/COLOR]

---

### Post by oldfred on 2024-09-15
Is this an HP system?
HP does not seem to accept changes from efibootmgr which grub uses to change boot order on install or update. It seems to auto reset to Windows.

Those with HP and a few others say to change boot order in UEFI settings (not one time boot menu).

---

### Post by tea for one on 2024-09-15
Good afternoon

A very peculiar issue...............?
I think that you should try to set your efi entries for Ubuntu and Windows as active and the offending entry as inactive.
Section 5 here [https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples](https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples)

---

### Post by chetinho10 on 2024-09-15
[COLOR=#000000]Good afternoon

It is not an HP computer, it is a computer assembled by parts.

Greetings[/COLOR]

---

### Post by chetinho10 on 2024-09-15
> **tea for one said:**
> Good afternoon

A very peculiar issue...............?
I think that you should try to set your efi entries for Ubuntu and Windows as active and the offending entry as inactive.
Section 5 here [https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples](https://www.linuxbabe.com/command-line/how-to-use-linux-efibootmgr-examples)


Thank you so much.


I'll try it later

---

