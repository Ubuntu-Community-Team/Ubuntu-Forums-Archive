---
title: "Dual boot W7 and 14.04, dual hdd. How to install fresh 18.04."
date: 2018-09-29
forum: General Help
---

### Post by hiloguy on 2018-09-29
My Dell laptop has a 128Gb ssd with w7 and a 500 Gb SATA drive installed in an optical drive adapter. The 500 Gb drive has 14.04.  The machine boots to a select screen and goes to Ubuntu by default unless I select W7.  My 14.04 still works, but has more and more "errors" and I'd like to do a fresh install of 18.08 (which I have ready on a USB drive) without messing up the boot sequence!  

Please walk me through the correct procedure so I won't mess this up by guessing!  I use Ubuntu for everything except the occasional Windows-required thing like updating our GPS's, etc. All of my Ubuntu data files are safely copied to Dropbox.

:)

---

### Post by oldfred on 2018-09-29
Is select screen your BIOS/UEFI or grub boot menu?

Best to see details.
       Just run the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Are you able to boot from HDD? Many cannot boot another drive in DVD drive slot, only from internal drive.

Which model Dell?
 Older BIOS system?

---

### Post by hiloguy on 2018-09-30
> **oldfred said:**
> Is select screen your BIOS/UEFI or grub boot menu?

Best to see details.
       Just run the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Are you able to boot from HDD? Many cannot boot another drive in DVD drive slot, only from internal drive.

Which model Dell?
 Older BIOS system?


The laptop is a Dell E6420.   I'm having no issues with the computer and it always boots properly, default into Ubuntu and on the select screen it boots into W7 if I select it.  I'm enough of a novice (after ten years of using Ubuntu for just about everything!) that I cannot tell you if the select screen is BIOS/UEFI or grub boot menu.  If I had to guess, I'd say grub boot menu.  It's a purple screen with a very small list of the four boot options in the upper left corner, if that helps.

This computer boots exactly like another one I use that is dual boot but has only the one HDD. I actually don't know which drive this one boots from.  W7 was on the computer when I bought it and I installed Ubuntu the way I've always done it in the past, just set the computer to boot from the USB drive.  

So everything is working as it should, but I just want to do a fresh install of 18.08 over my 14.04.  I've tried to boot to the USB with 18.08 ready to go, but after selecting USB from the F12 boot sequence menu, it still will not boot.  So I'm thinking I need to do this from the Ubuntu drive and not from the W7 drive?

Thank you!

---

### Post by ajgreeny on 2018-09-30
We still need you to run **Boot-Repair** as mentioned by oldfred and follow the instructions there to run the Boot-Info-Script.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system. 
It sounds as if you have a BIOS setup but let's be sure.

---

### Post by oldfred on 2018-09-30
It should just boot from f12 BIOS/UEFI boot menu.

But many Dell need BIOS/UEFI updates and many SSD need firmware updates.
But if older install works, I am a bit surprised that newer version does not at least boot.

Issue could be the major changes that UEFI/BIOS, Windows & Linux kernel & firmware have had to make for this:
[https://blog.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities](https://blog.ubuntu.com/2018/01/04/ubuntu-updates-for-the-meltdown-spectre-vulnerabilities)
And I think the updates must be all applied for system to work.

---

### Post by hiloguy on 2018-09-30
***It should just boot from f12 BIOS/UEFI boot menu.***

Here are you referring to booting from the W7  F12 boot-selection?



[B][I]Issue could be the major changes that UEFI/BIOS, Windows & Linux kernel & firmware have had to make for this:
[https://blog.ubuntu.com/2018/01/04/u...ulnerabilities](https://blog.ubuntu.com/2018/01/04/u...ulnerabilities)
And I think the updates must be all applied for system to work.[/I][/B]

This may be the key to the problem.  I mentioned my 14.04 is occasionally reporting unresolvable errors.  One of them is that it will no longer do updates.  When I try to accept an update and to install it, I get an error message.  It just asks whether or not I wish to report the error.

So is there a way I could just delete the contents of all the partitions on the SATA drive installed in the optical drive bay (the drive that has Ubuntu 14.04 on it, and then install 18.04 onto that same drive by booting to USB from the W7 boot selection (F12)?  That's how I did it originally.  I'd like to leave the partitions intact, as they were carefully set up specifically for this two-drive system.  I was trying to keep things simple, but alas, such doesn't seem to be the case.

What if I removed the optical-drive/SATA drive from this laptop, insert it into another Dell laptop (I have several), and installed 18.04 to it.  Would it then work when re-installed in the original laptop?  

I thank you for your patience; although I've been using Ubuntu successfully for over 10 years, I have not (had to) master the intricacies of internal workings!  I'm trying, though!

---

### Post by oldfred on 2018-09-30
You boot install media from UEFI/BIOS boot, that is often f12 with Dell, not from within Windows.

---

### Post by hiloguy on 2018-10-01
F12 reliably brings up the boot menu in W7, but when I try it while Ubuntu is booting up, I get this:  **^[[24~**

When I rand the sequence to determine UEFI/BIOS, the string I was supposed to find in Panther is not there.  

I'm not an Ubuntu wizard, so this is always a learning experience for me.  There just has to be a simple way to accomplish this.  This is an old Dell E6420.  I'm used to using BIOS to order boot sequence, have never even heard of EUFI before.  How about if I remove the SATA drive in the optical-drive bay, format it in another computer, reinstall it and then can I just install Ubuntu 18.04 from Windows the way I've done this on half a dozen dual-boot machines in the past?  The only difference is that I'm using two hard drives on this one.  The SATA drive is reserved for Ubuntu only.

The current 14.04 on this machine is buggy, and that's why I want to do a clean install of 18.04.  The 14.04 will not open "system settings" or most of the other drop-down items, and it will no longer accept updates.  It just gives me error messages.  That's the reason for the switch to 18.04.

---

### Post by oldfred on 2018-10-01
You may also need to update BIOS from Dell.

The only version of Ubuntu that installed from inside Windows was Wubi. And last supported version of wubi was 12.04, but it was available in some newer versions.

May be best to see details:
       Just run the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by hiloguy on 2018-10-01
I tried installing boot-repair through Terminal but each of the second two entries returned errors and it would not install.  I can boot into either Ubuntu or W7 just fine right now, so what I would really love to be able to do is to clean off Ubuntu from the SATA drive in my optical bay and start from scratch instead of trying to fix 14.04 which I want to replace with 18.04 anyway.  My concern is that if I wipe that drive, will I even still be able to boot into W7 (on the main HDD), or will removing Grub from the second drive mess that up?  Seems I did this once before and it was a nightmare.

---

### Post by oldfred on 2018-10-01
That is where we need more details.
Are you using Ubuntu live installer in live mode?
What errors then are you getting on installing ppa and running Boot-Repair?
Is Internet working, that is required.

---

### Post by hiloguy on 2018-10-01
**Are you using Ubuntu live installer in live mode?**

The 18.04 I want to install has been installed via disk creator onto a thumb drive.  I downloaded 18.04 from the Ubuntu download site and this copy contains WUBI. 
When I hit F12 on (Ubuntu) boot-up, I get this:  **^[[24~**

**What errors then are you getting on installing ppa and running Boot-Repair?**

I could not install Boot-Repair from Terminal.  The commands I copied from the instructions would not run.  A lot of things in this buggy copy of 14.04 don't work anymore, which is why, after running it without a hitch for several years, I want to upgrade to 18.04. I really don't want to fix 14.04; I just want to upgrade to 18.04.  Isn't there a way to do this without going through all of this "repair" experience?  Both Ubuntu and W7 boot up fine.  The only problem is that I need to replace this copy of 14.04.

**Is Internet working, that is required.**

Internet is working fine.

---

### Post by oldfred on 2018-10-01
Please see this:
**[SIZE=1][FONT=arial]Forums Staff recommendations on WUBI[/FONT][/SIZE]**

[https://ubuntuforums.org/showthread.php?t=2229766](https://ubuntuforums.org/showthread.php?t=2229766)

---

### Post by hiloguy on 2018-10-01
Wow.  Why would Ubuntu discontinue WUBI, when it has worked so well to get so many new people to start using the OS?  So is there now an improved way to install Ubuntu, with or without a dual boot?

---

### Post by QIII on 2018-10-01
Ubuntu is an operating system.

Canonical, the company that produces Ubuntu, did not discontinue WUBI.  The WUBI developers ceased development on it.  So Canonical no longer includes it.

WUBI didn't work well with UEFI. There is an unofficial fork for UEFI, but I'm not sure where to find it.

You can, as you always could, dual boot.  If you don't want to reboot, you can, as you always could, run Ubuntu in a virtual machine on Windows.  Nothing new there in either case.

There are people who keep WUBI limping along out there, but I have to wonder what the point is.

---

### Post by hiloguy on 2018-10-02
OK, I get that.  But what is the alternative for Ubuntu enthusiasts like me, who have been using it for many years with no problems, and now wish to perhaps configure another computer with a fresh install?  There used to be alot of help here for newbies on using WUBI for a trouble-free, simple install.  Can you direct me to instructions on how to do this without using WUBI?  

Thank you, and everyone else here, for your patience and assistance!

---

### Post by oldfred on 2018-10-02
The original developer of wubi, only expected users to use it for a short time. At next release of Ubuntu or less than six months.

Now we have live installer on flash drive. While not as fast loading, once in memory it works just as fast. And if not just testing you can add persistence to save some data. But live installer is not up-datable.

All new computers (Since Windows 8 in 2012) are UEFI with gpt partitioning. Standard Wubi did not work with gpt, so could not be used with any newer computers. 
Part of reason for wubi, was the MBR limit of 4 primary partitions. But with new systems and gpt,  there is not really any limit on partitions. 

As QIII mentioned, some have forked wubi and made it to work.

---

### Post by QIII on 2018-10-02
Without using WUBI, you can install to a thumb drive, dual boot or install in a virtual machine.  Those are the basic choices.

---

### Post by hiloguy on 2018-10-05
I FIXED IT!  So after trying all of the above fixes to the best of my limited Ubuntu-awareness, I went for simple.  This has served me well so far with other issues over the years.  I gathered from some of the replies that there may have been something wrong with my 18.04 USB drive.  I had created the drive in Ubuntu, so this time I created another one in W7 using RUFUS.  It worked.

Thank you all for your assistance, and I'm thrilled to now have 18.08 on my laptop, running sweetly!

---

