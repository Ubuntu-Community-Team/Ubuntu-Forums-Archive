---
title: "Stuck in GNU GRUB terminal, cannot boot into Ubuntu 14.04 LTS"
date: 2016-01-04
forum: General Help
---

### Post by Javaisnom on 2016-01-04
This is a bit long and may contain some noobiness, but please bear with me.

After rebooting my PC, I was met with an error, "Unable to mount /". The session prior I made my partition writable and readable, which it wasn't for some reason.

After the kubuntu splash, it said it cannot mount / (the root directory).  I then tried to reinstall grub to /dev/sda, thinking it resolve the issue, ignoring the warning about not running on a livecd.

 I booted into a grub terminal, restarted, and went into my BIOS, turned off safe boot after reading it could solve this issue. It didn't, and that's where I am now, stuck with my GNU GRUB terminal and a likely botched HDD. 

Thank you for reading all of this, and I'd be very appreciative of any assistance you can offer!

- Java

---

### Post by Javaisnom on 2016-01-04
[http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows](http://askubuntu.com/questions/88384/how-can-i-repair-grub-how-to-get-ubuntu-back-after-installing-windows)

 I ran the commands listed in the top reply, which is what I meant when I said 'reinstalling grub to /dev/sda/.'

I'm still hoping for some responses, thank you very much in advance!
-Java

---

### Post by dragonfly41 on 2016-01-04
The post you refer to suggests using boot-repair while in Live USB/CD.

Probably you will need to install "boot-repair" app into your Live USB/CD.

Search for the download/install link.

---

### Post by grahammechanical on 2016-01-04
> I booted into a grub terminal, and went into my BIOS,

No you didn't. It is impossible to enter the motherboard BIOS setup utility from the Grub boot menu. The function is not available. We enter the motherboard boot system (BIOS or UEFI) settings utility before the Grub boot menu loads. Usually, about the time the motherboard splash screen appears.

Is the Grub boot menu loading? If the answer is, yes, then Grub is installed. What happens when you select an OS to load? "I was met with an error" is not sufficient information to describe the problem or indicate where the problem occurs. What is the error?

Can you get to a login screen? If the answer is, yes, then there is no problem with Grub or with secure boot. Again, what is the error?

Solutions to other people's problems are only appropriate if we have exactly the same problem. Otherwise we risk causing more problems and we head closer to a reinstall as the easiest option. 

So, please describe what happens when you select an OS to load. Please describe the hardware and the operating systems on the computer.

Regards.

---

### Post by Javaisnom on 2016-01-04
Grahammechanical,

I rebooted, pressed the F12 key after the mobo splash screen, and then disabled secureboot.
I am in the GNU GRUB terminal, not the GRUB bootscreen.

Upon booting my Ubuntu partition (not from the grub bootscredn), the only thing onscreen is a GNU GRUB terminal, the terminal with "minimal BASH-like line editing supported". I assume I would either need to reinstall and/or use boot repair now. I'll provide hardware details now, thank you.

---

### Post by Javaisnom on 2016-01-04
Dell Inspiron 7548 (laptop) - Intel(r) core i7-5500U cpu 2.40 ghz, came with Win 8.1.

---

### Post by yancek on 2016-01-04
> The session prior I made my partition writable and readable, which it wasn't for some reason.

Which partition and what was the exact command you used?  The / (symbolic for the root partition) needs certain owner:group and permissions.  As a general rule, anything outside the /home/user directory will be owned by root.  Without more info on what you did, not much anyone can do to help.

---

### Post by dragonfly41 on 2016-01-04
Please read your apparent symptoms here .. and how to install/apply boot-repair

[http://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/](http://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/)

---

