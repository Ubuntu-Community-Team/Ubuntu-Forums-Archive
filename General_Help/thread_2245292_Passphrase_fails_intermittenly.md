---
title: "Passphrase fails intermittenly"
date: 2014-09-22
forum: General Help
---

### Post by tuxbonewits.com on 2014-09-22
I've been computing since 1984.
I've been using Ububtu 14.04 since May.
Having a re-occuring problem with the passphrase on startup.
Every seven or eight days the passphrase will fail.
I have to re-start and do a restore ubuntu and then during the restore process it accepts the passphrase.
When it starts something else is not working. 
Today it was eth0 could not be found. Last week it was Foxfire, before that it was wifi.

What do I need to do to solve the failing passphrase problem?
What data do you need to help?

###########################################################################

[COLOR=#000000][FONT=Times New Roman]HP Pavillion g7 - 2269wm[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]AMD Quad-Core A8-4500M Accelerated Processor[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]17.3" diagonal HD+ BrightView LED Display[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7640G][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]500 GB HDD[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]DVD A DS8A9SH[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]6144MB DDR3 SDRAM[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]DVD Optical Drive[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]20140801 - Ubuntu 14.04LTS Trusty Tahr OS[/FONT][/COLOR]

---

### Post by ajgreeny on 2014-09-22
Is the "passphrase" you talk of your normal user password needed to login, or are you asking about an encryption passphrase needed to boot, or perhaps a wireless connection password/passphrase?

More info please.

---

### Post by grahammechanical on 2014-09-22
> [COLOR=#000000]I have to re-start and do a restore ubuntu and then during the restore process it accepts the passphrase.[/COLOR]

I am curious. How do you restore Ubuntu? I suspect that there is more wrong with your system than this problem. Did you install Ubuntu using wubi.exe? Are you using some Windows Restore facility?

Regards.

---

### Post by tuxbonewits.com on 2014-09-22
for ajgreeny: encryption passphrase needed to boot


for grahammechanical: I mistakenly called it Restore. I ment Recovery




Soon after powering up the laptop I get the following prompt;
Unlocking the disk, Enter passphrase




When it will not accept my passphrase at the prompt, I have learned to do the following;


I hold down the power button until the laptop quits all pretence of starting.
I usually give it another 10 seconds or so.
Then press the start button and press Escape immediately.
It gives me the Start up Menu. 
I get the following; GNU GRUB Version 2.02~Beta...
*Ubuntu
 Advance Options for Ubuntu...
 System Setup
I select Advanced Options...
One of the options is press F11 - System Recovery (NOT reset as stated earlier)


When I press F11, I get  Advanced Options as follows;
*Ubuntu, with Linux 3.13.0-32-generic
 Ubuntu, with Linux 3.13.0-32-generic (Recovery)
 Ubuntu, with Linux 3.13.0-16-generic
 Ubuntu, with Linux 3.13.0-16-generic (Recovery)


I chose; 
 Ubuntu, with Linux 3.13.0-32-generic (Recovery)
Start up continues and I am once again asked for my passphrase
which is accepted and I'm good for about a week or so.
######################################################################################

[COLOR=#000000][FONT=Times New Roman]HP Pavillion g7 - 2269wm[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]AMD Quad-Core A8-4500M Accelerated Processor[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]17.3" diagonal HD+ BrightView LED Display[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7640G][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]500 GB HDD[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]DVD A DS8A9SH[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]6144MB DDR3 SDRAM[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]DVD Optical Drive[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]20140801 - Ubuntu 14.04LTS Trusty Tahr OS[/FONT][/COLOR]

---

### Post by tuxbonewits.com on 2014-09-29
Well, I can see from the overwhelming response, that this is not a common prob.
OK, guess I'll have to learn how to live with it :)

I have had a lot of success fixing other things, thanks to the forum & google =winning combo.
I'm gunna mark this solved as I can see no sense in leaving it open.

[COLOR=#000000][FONT=Times New Roman]HP Pavillion g7 - 2269wm[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]AMD Quad-Core A8-4500M Accelerated Processor[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]17.3" diagonal HD+ BrightView LED Display[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7640G][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Advanced Micro Devices, Inc. [AMD/ATI] Trinity HDMI Audio Controller[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]500 GB HDD[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]DVD A DS8A9SH[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]6144MB DDR3 SDRAM[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]DVD Optical Drive[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]20140501 - Ubuntu 14.04LTS Trusty Tahr OS[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]------------------------------------------[/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]A computer without Microsoft is like [/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman]a chocolate cake without mustard.[/FONT][/COLOR]

---

### Post by Vladlenin5000 on 2014-10-05
It is a common problem actually. If you have special characters in your passphrase and you have a keyboard other than US (or a US keyboard layout and a UK region setting). There's a bug changing the keyboard layout unexpectedly.

Try setting up a passphrase using only a combination of uppercase and lowercase letters and numbers while long enough to be secure. and the symptom shouldn't occur.

---

