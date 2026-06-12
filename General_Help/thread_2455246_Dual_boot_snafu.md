---
title: "Dual boot snafu"
date: 2020-12-15
forum: General Help
---

### Post by pjnoxon2 on 2020-12-15
I have a Thinkpad T450 I bought at Fry's with 320Gb SSD, it came with Windows 10.
So I set it up dual boot by meddling with the partitions and put Ubuntu Studio on it.

It has been working just fine for several months, but now the Windows 10 hangs up
when I choose that. It was working fine before, but I think something went wrong
during a Windows 10 update. (Yes, I should have turned off the automatic update.)

I don't really want to start over. I think there should be a way to fix Windows 10
without killing Ubuntu Studio. Anyone have some experience with this?

When I boot into Windows 10 (on /dev/sda1) it acts like normal which is a blank
screen followed by a scrambled screen (it always did this briefly) and at first it
went into Windows but I couldn't do anything like it never finished booting, and
now it just stays on the scrambled screen. And no there is no CD/DVD drive.

---

### Post by pjnoxon2 on 2020-12-15
At the scrambled screen if I press Ctl-Alt-Del then it will 'reboot'
but not to the Grub but a screen that says:

error: no such partition.
Entering rescue mode...
grub rescue> _

---

### Post by oldfred on 2020-12-15
Are you trying to boot Windows from grub or UEFI?
If grub, try UEFI.

Grub only boots working Windows. And that means fast start up/ hibernation must be off and NTFS cannot need chkdsk.
Windows does turn fast start up back on with updates, so if Windows updated that could be the issue.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by pjnoxon2 on 2020-12-15
The Lenovo came with Windows 10, I partitioned and installed Ubuntu Studio.
This means it is UEFI I am pretty sure. I don't know what you call the screen
where you choose Ubuntu - or - Windows - or - one of the memtest86+

Is that not called Grub? It says Grub

I was looking at the Lenovo just now, and it went into Windows after the
scrambled screen, and now it says "Preparing Automatic Repair"

it looks like it is stuck on that screen

I went into the "BIOS" and turned off the "Intel Rapid Start" which was on.

Now when choosing Windows on the menu that says "Grub Boot Menu"
it is stuck at the scrambled screen again. If I Ctl-Alt-Del now it says:

error: attempt to read or write outside of disk 'hd0'.
Entering rescue mode...
grub rescue> _

I try to choose Ubuntu each time, it is still working OK

---

### Post by tea for one on 2020-12-16
You can make a bootable USB stick containing a Windows 10 ISO and use it to try and repair your Windows OS.

Any Windows repair could also create other unexpected dual boot problems such as interfering with Grub.

When you boot the ISO, there is a choice to repair in the screenshot attached:-

Also, I hope that you have backups of your personal data.

---

### Post by oldfred on 2020-12-16
You have two boot menus, UEFI has one & grub has the other.
Windows should boot from UEFI boot menu, if Windows turned fast start up on. Error you are getting is typically for that being the issue as grub will not boot hibernated Windows & fast start up sets hibernation flag.

Directly boot Windows from UEFI & turn off fast start up.
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Lenovo ThinkPad X1 Extreme 2019 UEFI settings required.
[https://askubuntu.com/questions/1291280/after-running-boot-repair-and-disabeling-secure-boot-still-not-booting-to-grub](https://askubuntu.com/questions/1291280/after-running-boot-repair-and-disabeling-secure-boot-still-not-booting-to-grub)

UEFI update required for USB-C port issues 2017 thru 2019 models
ThinkPad models including the ThinkPad X1 Carbon (5th Gen to 7th Gen), X1 Yoga (2nd Gen to 4th Gen), and P-series 
[https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/](https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/)

Note that UEFI updates may reset some UEFI settings (like Intel RST/AHCI), do double check those after any update. I have to keep a list for my motherboard as it changes a number of settings.

---

### Post by pjnoxon2 on 2020-12-16
The only menu I have ever had when booting up cold is the one that says Grub.
There has never been any other start up menu, only the one that says Grub.
I have never seen any other start up menu ever, like one that says UEFI or any
other start up menu only -> the one that I refer to in all posts, it says Grub.

Now everytime I had booted into Windows in the past (when it was working)
it would follow Grub boot menu with a scrambled screen and then go into
Windows. Is it possible that scrambled screen is some other boot menu?

I don't see anything that says fast start, only the BIOS setting for Intel Rapid Start.

I tried to use the hibernate once a year ago and since it didn't work I have always
shut down the laptop whether I was using Windows or Ubuntu Studio. Later when
I press the power button it will always go to the menu that says Grub. I  decided
to try hibernate by closing the lid while Windows was running that one time a year
ago, and since it did not work I always manually choose shut down and wait for it
to power down before I close the lid. The system is never hibernated. It doesn't work.

I can't get into Windows, that is the problem, so suggestions to do something from
Windows are impossible. I have not really done too much with this laptop, it is a
spare. I have installed Mixbus6, Wireshark, and Thunderbird in Ubuntu Studio.
I also installed the toolchain for working with a STM 32H750IBK6 SOC project.
 I will run Thunderbird in the morning just to check my e-mail accounts, but I
don't usually answer e-mail on the Thinkbook, just check messages. Later when
I have had my morning Capuccino I will answer e-mail on my Zenbook.


I have a 7 year old ASUS running Windows 7 and Ubuntu Studio, and it
works fine in both, I think because I turned off the automatic update in Windows.
I bought the Thinkbook to replace that ASUS someday, it is over at my office.
I also have an ASUS Zenbook that runs only Windows 10, so I left auto update on.

The laptop is a Thinkbook T450, it is not an X1, an X1 Extreme, does not have
USB-C, and I have not updated any BIOS stuff.

Lenovo T450 BIOS Screen

UEFI BIOS version    JBET73WW (1.37)
UEFI BIOS Date        2019-8-14
i5-5300U CPU
Preinstalled OS License    SDK0E50510 WIN
OA2            Yes

I was planning to make a Windows 10 rescue USB drive but it crossed my
mind that this would wreck the Ubuntu Studio installation. Since it is more
important to me than Windows, I have put it off. Just looking for someone
who had similar experience to get some advice before I do anything else.

---

### Post by oldfred on 2020-12-16
Normal shutdown in Windows is fast start up on. 
You have to change settings as shown in links.

With UEFI, you have an UEFI boot menu.
UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

It looks like you have to use f12.
Lenovo 
BIOS Utility F2 or blue &#8220;Thinkpad&#8221; button
Boot Menu F12

If you have fast boot on in UEFI, you may not have time to press any key to get into UEFI or UEFI boot menu at f12.

---

