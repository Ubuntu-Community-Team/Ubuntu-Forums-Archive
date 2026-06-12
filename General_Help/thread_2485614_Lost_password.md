---
title: "Lost password"
date: 2023-04-03
forum: General Help
---

### Post by rwichmann0 on 2023-04-03
I installed UBUNTU on my HP Touchsmart with the undestanding I would still be able to access Windows. Unfortunately that isn't the case.

The situation now is I've forgotten/misseplaced my password. The question is is there ny way to recover it or install a new one or am I screwed?:(:-({|=

---

### Post by oldfred on 2023-04-03
What password?
UEFI, Ubuntu, Ubuntu installed with full drive encryption, or Windows bitlocker?
Not sure what others may also have passwords.

Generally you want to have good backups before any system change.

---

### Post by yancek on 2023-04-04
> I installed UBUNTU on my HP Touchsmart with the undestanding I would  still be able to access Windows. Unfortunately that isn't the case.
 

I'm sure you are aware that millions of users have been dual booting windows/Linux for 30 years so something obviously went wrong with the install.  As asked in post 2, you need to specify which password you mean.  It would also help if you indicated which windows version you are using and whether it is UEFI or Legacy.

---

### Post by ActionParsnip on 2023-04-04
[https://www.psychocats.net/ubuntu/resetpassword](https://www.psychocats.net/ubuntu/resetpassword)

---

### Post by rwichmann0 on 2023-10-08
I have a HP Touchsnart with OS Windows 11 Home running Ubuntu 10.10 and have forgotten my password. I understand it is not recoverable. When in wondows I thought I'd check out Ubuntu with the ubderstanding I'd be able to switch between them whenever I wanted to but there seems to be no way to do that nor am I able to access the internet.

I have another HP Touchsmart running Windows 11 Home. I'd like to use both computers one with Windows and the other with Ubuntu. How can I reload and set up Ubuntu again without purchasing a disk? Or is there some other soluton?

Hope someone can help me with this ***problem.***

---

### Post by oldfred on 2023-10-08
What version of Ubuntu? If system supports Windows 11, Ubuntu 10.10 would not work.
I think HP is the least friendly to Linux installs, and requires a bit more effort to work.

Make sure you have latest UEFI firmware & if SSD, latest firmware for it.
You have to have Windows fast startup & bitlocker off to dual boot from grub menu. But should be able to always dual boot from UEFI boot menu. Both installs must be in UEFI boot mode. Often easier with UEFI Secure boot off.

If you want Ubuntu as default, you typically have to go into UEFI settings (not UEFI boot menu) and in boot tab change boot order.
HP seems to be only vendor that does not support boot order change with efibootmgr which during install grub uses to reset to make Ubuntu first. But both Windows & Ubuntu on major updates may change boot order to make their install first in boot order.

---

### Post by MAFoElffen on 2023-10-08
I think I need to add that Oldfred also meant you need to be using a Current Supported version of Ubuntu, such as 22.04 LTS. Was the version posted a typo? 

If it was a typo, and current, then in the Grub2 menu > Advanced Options > Select a kernel with "Rescue" > network to mount the filesystem i r/w > root to drop to a root prompt...

At the root prompt:
```

passwd <user_name>

```
Such as if your user_name is "rwichmann0" then it would be
```

passwd rwichmann0

```
Type in and confirm the password to reset it...

If it wasn't a typo, download and create an Installer LiveUSB from an Ubuntu 22.04.3 LTS ISO. Booted from it, read and backup the data that you wabt to save from it, onto something else (USB attached drive). Install 22.04.3 LTS.

---

### Post by ajgreeny on 2023-10-09
Is this thread a continuation of the one you started back in April [https://ubuntuforums.org/showthread.php?t=2485614&p=14137442#post14137442](https://ubuntuforums.org/showthread.php?t=2485614&p=14137442#post14137442) with a similar title?

You did not return to that one after several suggestions and replies so it may be useful to merger these two threads so we all know where we have got to with the problem.

---

### Post by yancek on 2023-10-09
> When in wondows I thought I'd check out Ubuntu with the ubderstanding I'd be able to switch between them whenever I wanted  

I'm not really sure what you mean by the above because a default windows will not recognize a Linux filesystem nor be able to read or write to it.  If it is a matter of a forgotten password for whichever Ubuntu release you have, that is another question. 

> I have another HP Touchsmart running Windows 11 Home. I'd like to use  both computers one with Windows and the other with Ubuntu. How can I  reload and set up Ubuntu again without purchasing a disk? 

Did/do you have Ubuntu on the same computer on which you have windows?  Does the second computer not have a hard drive?  I don't really understand the problem.

I don't believe there is a way to boot both windows 11 and any Linux on a UEFI machine from windows but you can from Linux/Ubuntu with Grub.  I think you need to clarify your situation and exactly what you want to accomplish.

---

### Post by oldfred on 2023-10-09
Threads merged.

---

### Post by ActionParsnip on 2023-10-09
[https://www.psychocats.net/ubuntu/resetpassword](https://www.psychocats.net/ubuntu/resetpassword)
Explains it well

---

### Post by MAFoElffen on 2023-10-09
Although, from what you described...

If you want to stay within Windows 11 Home, and be able to jump between Windows and Ubuntu without having to reboot, you need to think about that a bit differently.

If you install VirtualBox or VMware Player to Windows, then you could install Ubuntu to one of those as a Virtual Machine Guest.

Then you would have the ability to "jump between" the Windows Desktop and the running VM Guest. That way you can have both running at the same time.

---

### Post by rwichmann0 on 2023-10-10
I apoligize for not getting back sooner, and than you all for responding, unfortunately none of them was of much help. Maybe I over stated the problem or wasn't really clear as to what I intended.

Will I have to reinstall Ubuntu and if so will it take a disk (I can't deleat it) and am a little concerned about connecting to this computer via USB or Lan. Bottom line is all I want is to undo whatever I did to screw it up and getting it running as it should.

Again I want to thank everyone for responding to my post, Robert

---

### Post by ActionParsnip on 2023-10-11
You can chroot into the installed OS from Ubuntu live USB/CD desktop and repair the system there too. Chroot is a great tool

---

