---
title: "Trying to Install Ubuntu to dual boot from windows 10 - getting nowhere :/"
date: 2016-12-17
forum: General Help
---

### Post by pweyand on 2016-12-17
Hey everyone, I am a complete newbie, and I am stuck trying to even install Ubuntu. I have a dell xps 15 and I've, so far, turned off fast boot and secure boot in the bios as well as created a partition in the windows manager. I installed the Ubuntu 16.04.1 distro on a thumb drive and successfully got that to run on "try Ubuntu" mode. However, when I try and install through the manager while I'm in "try" mode all that Ubuntu can see is the thumb drive - it can't see my hard drive at all. Totally lost on what to do - as far as I can tell this problem hasn't been addressed in any of the online documentation or tutorials. Can anyone please help?

---

### Post by cdtech on 2016-12-17
This gives you step by step instructions on installing Ubuntu along side Windows.

[https://www.ubuntu.com/download/desktop/install-ubuntu-desktop](https://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

Hope that helps, if not let us know.........

---

### Post by pweyand on 2016-12-17
I never get to step 3 in the installation setup, and the next step after that (which is not shown) where you are to allocate drive space and choose the installation boot space only sees my USB stick. Sorry, that doesn't help me.

---

### Post by RobGoss on 2016-12-17
Hello and welcome, Are you able to see the option **something else? **if so choose this option and choose the **unallocated space **you created to install Ubuntu, you will also have to crate a swap partition as well, this guide should help you get started: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

**GRUB** needs to be installed into the MBR, **Master Boot Record **of your hard drive it will detect **Win-10 **and automatically include it as a boot option.

[B]
Instructions on how to dual boot Windows and Ubuntu[/B]
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by yancek on 2016-12-17
If you are using windows 10 currently, it is important to know whether it is UEFI or and older MBR install.  Pre-installed windows 8/10 are almost always UEFI.  See the Ubuntu documentation below on dual booting windows/Ubuntu UEFI.  If you do have an EFI windows install, you need to boot Ubuntu EFI to install or the results will be problematic.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

In your post you indicate you created a partition in windows on which to install Ubuntu.  Not much point in that.  You are better off shrinking the windows partition(s) and leaving uncallocated space on which to install Ubuntu.  You will need to format the partition using a Linux filesystem during the install anyway and a default windows is incapable of doing that.  If you do have an MBR install, how many partitions do you currently have?

---

### Post by pweyand on 2016-12-17
RobGoss: No. Like I said the page that has the "something else" option with the radio buttons isn't even displaying. It simply skips that page. I haven't done the GRUB thing yet I'll look into that.

Yancek: It is UEFI installed. I already have followed an installation guide that makes you check that and deal with all the issues stemming from that. I have shrunk the windows partition before booting into Ubuntu. That's not the issue either.

---

### Post by oldfred on 2016-12-17
Did you turn off Windows fast start up or hibernation.
That prevents the Linux NTFS driver from seeing you have NTFS partition(s).
Windows on updates may also turn fast start up back on, so you may have to check regularly.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions)

---

