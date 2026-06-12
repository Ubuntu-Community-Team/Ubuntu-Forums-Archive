---
title: "Lubuntu GRUB 2 Install/Boot Repair Issue"
date: 2016-12-29
forum: General Help
---

### Post by Vladglot on 2016-12-29
I have successfully installed Ubuntu a handful of times on various machines. This time I've run into trouble. Just installed Lubuntu 16.04 on an HP Stream notebook via USB live disk. I've looked at several similar threads on the forums here but none held a solution for me. Here's what happened:

After installing Lubuntu, the installer crashed, giving me the error message that "grub-efi-amd64-signed' package failed to install into /target/" It also said "Please do not forget to make your BIOS boot on mmcblk0 (31.3 GB) disk! You may now reboot."

I rebooted and now have the "Minimal BASH-like line editing is supported" 

I've run boot repair several times from USB, to no avail.

Paste bin: [http://paste2.org/ddJJ6Ugw](http://paste2.org/ddJJ6Ugw)

---

### Post by oldfred on 2016-12-29
Your memory card is MBR(msdos) partitioned, but you booted repair disk in UEFI mode.
If you want an UEFI install card needs to be gpt partitioned.
Was it gpt before and how did you convert to MBR? Windows does it incorrectly.
And that may be this error where label is related to gpt or MBR:
> Error: /dev/mmcblk0rpmb: unrecognised disk label


       [http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook](http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook)

Are you able to boot the 64 bit version of Lubuntu.
Some Streams are 32 bit UEFI. These do not boot in BIOS/legacy mode.
[http://h30434.www3.hp.com/t5/Windows/Linux-on-the-HP-Stream-tablet/td-p/4829188](http://h30434.www3.hp.com/t5/Windows/Linux-on-the-HP-Stream-tablet/td-p/4829188) 

Do not know if then BIOS/MBR configuration would work better or not.

Update, see this also:
[http://h30434.www3.hp.com/t5/Windows/Linux-on-the-HP-Stream-tablet/td-p/4829188](http://h30434.www3.hp.com/t5/Windows/Linux-on-the-HP-Stream-tablet/td-p/4829188)

---

### Post by Vladglot on 2017-01-12
No, I did not convert the memory card on the Stream. It is possible to GPT partition it at this point?

I can boot the 64 bit version from disk, but not from the laptop once it's installed, because of the installer crash issue at the end. I did see that dual boot threat before on askubuntu, but I'm not dual booting and

---

### Post by oldfred on 2017-01-13
Does this Stream boot in both BIOS & UEFI boot mode without issue. And you can run live installer in live mode?

---

### Post by Vladglot on 2017-01-16
I'm not sure if it boots in both BIOS and UEFI. This is a little beyond me. I am able to run it in live mode; Lubuntu installs then we have the installer crash.

---

### Post by Vladglot on 2017-01-16
It sounds like your original message was that I would do better to have the memory card on the Stream gpt partitioned, right? Since I've taken Windows off the Stream already, can I do that from the repair disk? Should I get a different repair disk? Thanks, still lost.

---

### Post by oldfred on 2017-01-17
I thought these HP Steam only booted with a special 32 bit UEFI that is not included in the standard download. (as in link in post #2).

But if you can boot standard download in either BIOS or UEFI they have updated or changed hardware to be full 64 bit.
The 32 bit versions were UEFI Class 3 which means they have no CSM or no BIOS.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

If you have settings in UEFI to change from UEFI to CSM/BIOS/Legacy then it is not the 32 bit version.

This shows screen you see when you boot. How you boot installer is then how it installs.
      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Vladglot on 2017-01-22
I've solved it - the issue was a mistake I made with the file system partition. Thanks for your attention and help!

It is the 64 bit UEFI version and boots right up now.

---

