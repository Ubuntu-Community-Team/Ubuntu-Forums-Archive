---
title: "Can't install or upgrade to any OS except for Ubuntu"
date: 2014-06-15
forum: General Help
---

### Post by atomicsyntax on 2014-06-15
Hello,

I have tried for months researching to what feels has been a long road to nothing. I have learned a lot in the process, but not enough it seems to be able to fix my issue. I really hope this community can help me.

My computer Specs are:
Lenovo G480
Ubuntu 12.04.4 LTS
6GB RAM
intel core i3

My main issue is not with the OS itself(although I believe it's installation might have caused the problem), I have been using it since 10.4. Ever since I got this computer and installed a fresh Ubuntu 12.04 on it, my BIOS simply denies me entry. Every time I try to edit the BIOS for boot device priority, it ignores my inputs at the black splash screen. I have two options, I can either F2 to enter BIOS settings, or I can F12 which takes me to a "boot menu". I have tried multiple versions of multiple distros, on CD's, Live USB's, you name it. Every time I try to select a boot device from that menu, it also gets ignored and it boots straight to what I installed on the hard drive.

The only way for me to get anything working from the F12 boot menu is either a CD or a Live USB with an Ubuntu distribution on it. Nothing else will work, and it doesn't matter how old it is either. I have several backups of older versions just in case. With a 12.04 ISO, I have formatted several times, swapped hard drives, and I still have no access. I've tried installing Kali, but it won't recognize the Live USB, even though when I'm in Ubuntu browsing, when the USB is plugged in, you can clearly see everything was copied and set up properly.

I don't know if this is too vague, or too much, but please, if there's anything I can do to help, run commands, take screen shots, anything, please let me know. 

Thank you all so very much in advance, and I hope to talk to you all soon.

---

### Post by sandyd on 2014-06-15
> **atomicsyntax said:**
> Hello,

I have tried for months researching to what feels has been a long road to nothing. I have learned a lot in the process, but not enough it seems to be able to fix my issue. I really hope this community can help me.

My computer Specs are:
Lenovo G480
Ubuntu 12.04.4 LTS
6GB RAM
intel core i3

My main issue is not with the OS itself(although I believe it's installation might have caused the problem), I have been using it since 10.4. Ever since I got this computer and installed a fresh Ubuntu 12.04 on it, my BIOS simply denies me entry. Every time I try to edit the BIOS for boot device priority, it ignores my inputs at the black splash screen. I have two options, I can either F2 to enter BIOS settings, or I can F12 which takes me to a "boot menu". I have tried multiple versions of multiple distros, on CD's, Live USB's, you name it. Every time I try to select a boot device from that menu, it also gets ignored and it boots straight to what I installed on the hard drive.

The only way for me to get anything working from the F12 boot menu is either a CD or a Live USB with an Ubuntu distribution on it. Nothing else will work, and it doesn't matter how old it is either. I have several backups of older versions just in case. With a 12.04 ISO, I have formatted several times, swapped hard drives, and I still have no access. I've tried installing Kali, but it won't recognize the Live USB, even though when I'm in Ubuntu browsing, when the USB is plugged in, you can clearly see everything was copied and set up properly.

I don't know if this is too vague, or too much, but please, if there's anything I can do to help, run commands, take screen shots, anything, please let me know. 

Thank you all so very much in advance, and I hope to talk to you all soon.
Hi, how are you creating the Kali Live USB?

---

### Post by atomicsyntax on 2014-06-15
With dd command, as it's said to do in the Kali website.

---

### Post by atomicsyntax on 2014-06-15
> **sandyd said:**
> Hi, how are you creating the Kali Live USB?


With the dd command as it's mentioned in the Kali website.

---

### Post by grahammechanical on 2014-06-15
You have got me confused. First you say this:
> [COLOR=#000000]my BIOS simply denies me entry. [/COLOR][COLOR=#000000]

Then you say this:

[/COLOR]> [COLOR=#000000]I have two options, I can either F2 to enter BIOS settings[/COLOR][COLOR=#000000]

Does F2 open the BIOS settings utility? By the way, if you have Windows 8 installed then it is UEFI. And with Windows 8 machines we need a Linux distribution that will install a kernel that meets the requirements of Secure Boot. Ubuntu was secure boot capable in 12.10 and 12.04.2 also had it and every 64 bit version of Ubuntu since then. The reason why only Ubuntu 12.04 is installing could be because it is the only distribution you are using that meets the Secure Boot specification.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

This is the Lenovo solution for the F2 key failing to give access to the BIOS settings utility. But you say F2 works.

[http://mobilesupport.lenovo.com/us/en/documents/HT075709](http://mobilesupport.lenovo.com/us/en/documents/HT075709)

Regards.


[/COLOR]

---

### Post by atomicsyntax on 2014-06-15
> **grahammechanical said:**
> You have got me confused. First you say this:
[COLOR=#000000]

Then you say this:

[/COLOR][COLOR=#000000]

Does F2 open the BIOS settings utility? By the way, if you have Windows 8 installed then it is UEFI. And with Windows 8 machines we need a Linux distribution that will install a kernel that meets the requirements of Secure Boot. Ubuntu was secure boot capable in 12.10 and 12.04.2 also had it and every 64 bit version of Ubuntu since then. The reason why only Ubuntu 12.04 is installing could be because it is the only distribution you are using that meets the Secure Boot specification.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

This is the Lenovo solution for the F2 key failing to give access to the BIOS settings utility. But you say F2 works.

[http://mobilesupport.lenovo.com/us/en/documents/HT075709](http://mobilesupport.lenovo.com/us/en/documents/HT075709)

Regards.


[/COLOR]


F2 does indeed bring up the BIOS utility, but every time I try to get into it, it simply boots to the Ubuntu copy that's already in the hard drive. I don't have windows installed, I have only Ubuntu 12.04 LTS installed and nothing else. The entire OS is using the whole disk.

I will look into the F2 link you posted, but with out looking, I don't think it's what I need because I've been through that whole Lenovo support site with out any luck.

---

### Post by atomicsyntax on 2014-06-15
As far as grahammechanical's links go: The F2 one, that definitely doesn't work. Many people and sites have linked me to that with no luck. For the 2nd link, I can't do anything they're asking me to do there because I have no BIOS access. I cannot tweak or modify anything.

---

