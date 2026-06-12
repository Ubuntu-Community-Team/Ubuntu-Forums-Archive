---
title: "installed 22.04 on lenovo flex 3 - now no display"
date: 2024-02-07
forum: General Help
---

### Post by jdchurchill on 2024-02-07
hello pals- i decided to install ubuntu 22.04 on my POS lenovo flex 3. not dual boot just linux
and now i can get to BIOS and can't figure out how to get the machine to do anything else.
please help me troubleshoot as i would really appreciate utilizing this machine. it seems no matter what i do in BIOS the machine boots to a black screen. like no display. i can't get a terminal, typing does nothing. i have to push the power button to turn it off. and since installation i can't even get it to boot from the usb drive either. i am very frustrated

---

### Post by tea for one on 2024-02-07
> **jdchurchill said:**
> and now i can get to BIOS and can't figure out how to get the machine to do anything else.

Access UEFI settings and disable the following (if they exist on your PC)
Fast Boot
Secure Boot
TPM (Trusted Platform Module)
PTT (Platform Trust Technology)
FTPM (Firmware Trusted Platform Module)
TPT (Trust Platform Technology)
Device Guard (some Lenovo devices)
OS Optimised Defaults (some Lenovo devices)
Lock UEFI BIOS Settings
Boot Order Lock

---

### Post by jdchurchill on 2024-02-07
now i can't even get to the BIOS it just beeps and show a screen with the lenovo logo

---

### Post by tea for one on 2024-02-07
Do you have a Novo button?
[https://support.lenovo.com/gb/en/solutions/ht104038-where-can-i-find-the-onekey-recovery-novo-button-on-ideapad-laptops](https://support.lenovo.com/gb/en/solutions/ht104038-where-can-i-find-the-onekey-recovery-novo-button-on-ideapad-laptops)

---

### Post by jdchurchill on 2024-02-07
ya it's there i pushed it as far as i can tell a couple times with a paperclip. still just lenovo logo screen and now when i try Fn+F1 or F2 no beeps. ugh

---

### Post by jdchurchill on 2024-02-07
oh **** now i pushed the button and i got a screen with 'recovery boot menu' 
Normal startup
BIOS setup
Boot menu

---

### Post by jdchurchill on 2024-02-07
normal startup did not seem to be effective. select and just a blank screen, however now everytime i push that novo button i get the screen mentioned above.

---

### Post by jdchurchill on 2024-02-09
so as stated above the novo button works to get to BIOS. and as stated above normal boot does not resolve this issue. i have been mucking around in the BIOS a bit for only the same result: a black screen; can't get a terminal - just nothin 
please help

---

### Post by tea for one on 2024-02-10
> **jdchurchill said:**
>  i have been mucking around in the BIOS a bit for only the same result: a black screen;
"Mucking around" doesn't offer much of a clue, but, nevertheless, let's go back to square one.

Access your UEFI settings via the novo button.
Reset firmware to default

Then:-
Disable Secure Boot
Disable TPM
Disable any other Trust settings 

Enable USB boot as first priority
Attach your known working USB with Ubuntu 22.04 installer
Save settings and boot

What happens?

---

### Post by jdchurchill on 2024-02-14
so only thing that you mention i can change is disable secure boot. i could detail the options in the different categories in BIOS if you like. and thank you for taking the time to help me.
but now i've gotten to a gnu grub version 2.06 with the menu
*ubuntu or advanced options for ubuntu : lots of errors and bounced back to previous menu when ubuntu is selected. advanced options gives me another menu:
*ubuntu with linux 6.5.0-15 generic (or recovery mode), and ubuntu with linux 6.2.0-26 generic (or recovery mode)
no matter which one i select lots of errors : failure to read from 'hd0'

---

### Post by tea for one on 2024-02-15
Two skirmishes won so far:-
UEFI settings now accessible
Grub appears on the display

You tried to boot into your installed system and could not progress to your Desktop.
Likely due to corruption after this (from post 1) > i have to push the power button to turn it off
An ungraceful exit, when file systems are mounted, often causes damage.

Anyway, I suggest:-
Boot into a live 22.04 "Try Ubuntu" session in UEFI mode
Anything to backup - probably not?
Open Gparted
Create a GPT partition table
Close Gparted
Open the installer
Continue with your preferred choices

---

