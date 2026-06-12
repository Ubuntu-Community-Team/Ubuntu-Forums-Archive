---
title: "Problem when trying to boot linux with acer aspire E13."
date: 2015-06-05
forum: General Help
---

### Post by yerali on 2015-06-05
Hello, I have been trying to boot the computer into ubuntu, but I didn't succeed. I really need help.

I  have an acer aspire E13. And after disabled the boot-secure, I  installed ubuntu 14.04 alongside windows 8.1, I followed the procedure  with boot-repair but nothing change. I got the following message:

[http://paste.ubuntu.com/11591235/](http://paste.ubuntu.com/11591235/)
  

Please, I need hepl!!!!


Thanks in advance,

---

### Post by yancek on 2015-06-05
Are you able to boot windows?
What procedure did you follow?  Are you referring to the last part of the boot repair output beginning at line 1071 changing the boot order in BIOS?  What options do you have in your BIOS?

---

### Post by QDR06VV9 on 2015-06-05
You probably let bootrepair run the default repair, when you need to put grub in MBR
From your pastebin
> ============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

See this post #2 [http://ubuntuforums.org/showthread.php?t=2281043](http://ubuntuforums.org/showthread.php?t=2281043)

---

### Post by RobGoss on 2015-06-05
How did you install your Ubuntu live installation? DVD or USB drive

Why are you using boot repair I'm assuming your install did not go well.

---

### Post by oldfred on 2015-06-05
You have an UEFI system, so no boot loader in MBR is correct.

But you left Windows hibernation on. You need to go directly into UEFI, boot into Windows and make sure the always on hibernation or fast boot is off. And do full shutdown from Windows or it will still use fast startup.

 Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast startup is hidden.
If issues you may need these?
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavailable, make sure fast startup is unchecked 
powercfg /h off



And Acer require you to set a UEFI password (never ever lose that) and set trust for the ubuntu entry.

       Video on getting into UEFI - 1 Min Acer but similar to all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)
            Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)

            Acer E3 requires UEFI password to allow added settings Post #8
[http://ubuntuforums.org/showthread.php?t=2253311](http://ubuntuforums.org/showthread.php?t=2253311)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

---

