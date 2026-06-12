---
title: "USB devices"
date: 2004-11-26
forum: General Help
---

### Post by Jongi on 2004-11-26
Two fold problem:

**Part 1**
When I installed Ubuntu it picked up my USB modem. Since the install I've taken apart the computer to add another hard drive. However now I cannot see my modem. What could have happened?

**Part 2**
I suspect this is related to the problem above. When I stick a USB stick into the computer Ubuntu does not recognise it. If I reboot with it stucjk in, Windows XP will pick it up. Ubuntu does not. How can I rectify this so that I am able to see the USB stick.

---

### Post by astoltz on 2004-11-26
I've had all sorts of problems with my USB modem.  What Kernel version are you booting?  And what is the kernel module is your modem using?

---

### Post by Jongi on 2004-11-27
[QUOTE=astoltz]I've had all sorts of problems with my USB modem.  What Kernel version are you booting?  And what is the kernel module is your modem using?[/QUOTE]
 It's a 2.6.8.xxx kernel.

The modem I have is a Aztech 56k USB UM9100 modem using trhe drivers provided by [www.smlink.com](www.smlink.com). When I was using Mandrake 9.1 I had no issues installing it.

When I go to Device Manager there is no modem listed there but I know that after I had 1st installed Ubuntu a SG Thompson modem was listed (which was the case as well with Mandrake 9.1).

[LinuxQuestions.Org](http://www.linuxquestions.org/hcl/showproduct.php?product=1201) states that I should be able to use the driver I have with Kernel 2.6

---

### Post by astoltz on 2004-11-27
Sorry to say, it looks like your case is different than mine.  But I can suggest some places to start troubleshooting.

Look at the output of dmesg right after plugging in the modem.  You should see some messages that the modem was found and that the kernel loaded the correct module.  If you're lucky, it will even display the device node (/dev/usb/tty???).  Then it's just a matter of configuring the dial-up connection (I use pppconfig).

If gnome's device manager is not seeing it, then maybe dmesg (or maybe /var/log/syslog) will give you some hints as to what is going wrong.

Same goes for when you plug in any USB device. 

And just one last thing. Have you checked to be sure all cables are attached properly after you added the new hard drive?  Maybe you bumped the USB connector off it's slot on the mother board.

  -Al

---

### Post by Jongi on 2004-12-01
The USB devices are picked up in windows. I have re-installed since. Now I would like to know how I go about getting to dial up to my serice provider

---

### Post by Hendry on 2004-12-02
I'm also using the same kernel version on a 386 . I have no problem with my USB device. When I insert it it is discovered automaticly and I can use it right away

---

