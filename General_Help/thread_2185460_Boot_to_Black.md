---
title: "Boot to Black"
date: 2013-11-02
forum: General Help
---

### Post by smcb3357 on 2013-11-02
Good Afternoon ~ If this is not the correct forum for this issue, I will be happy to repost elsewhere. Anyway, I am a new Linux Ubuntu user. I had installed 12.04 and everything was running fine. Yesterday I started to upgrade to 12.10. The process was fine until the last step Restart. My laptop now boots to a black screen.

Specs: HP Pavilion TS 14 with AMD A8-5545m APU with Radeon Graphics.

Boot process looks like this: grey screen, purple, grey, black, grey, Ububtu splash screen, then BLACK.

I need help please. If this is a video driver issue, how can I set the correct driver from the command line. If a reinstall of 12.04 is required, how do I rescue my docs and files from the command line?

Thank you!

---

### Post by fantab on 2013-11-03
Sounds like a Graphcis, Radeon issue. Do you use any proprietory graphics drivers?

Try to boot with '[Nomodeset]("http://ubuntuforums.org/showthread.php?t=1613132")'.

---

### Post by smcb3357 on 2013-11-03
Good Morning ~ thank you for your reply. The instructions for 'Nomodeset' made sense however I cannot get to the grub configuration. Pressing Shift repeatedly during the boot process is not bringing it up.

---

### Post by ibjsb4 on 2013-11-03
When you get to that black screen, try pressing ..

Ctrl + Alt + F1

It may let you into terminal.

About what your doing, version upgrade.  Are you planning on upgrading until you get to 13.10?

If you do decide to go back to 12.04 ..
12.04 is an LTS, the next LTS is 14.04, coming out in April.  You can upgrade direct to the next LTS, skipping all the intermittent versions.  Maybe save yourself some upgrade grief.

You should be able to retrieve your files using the live CD.

I would also suggest that you create a data partition to store your files, music, videos.  This partition can be auto mounted and link to your running system.  Basically you don't know its there until you need it for recovery.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=data+partition&sa=Search&cof=FORID:9)

One last thought, the shift key should of worked.  Try just holding it down during boot.

Wait for others to reply, I am not good at trouble shooting video :)

---

### Post by smcb3357 on 2013-11-03
No luck with Ctrl + Alt + F1. Or, if it is starting Terminal, I cannot see it. No luck with holding down the Shift key either.

I agree about the partition and I'm looking forward to doing just that.

Could I get more details about retrieving files using the live CD? I am using a flash drive to install 12.04 from. Can I do the same thing from the flash drive? If so, I need a few clues how to do this, thanks! :)

---

### Post by Bashing-om on 2013-11-03
smcb3357; Hi !

As those 1st responders are currently off line, allow me to offer my assistance.
Back up, regroup and in small baby steps, let's see where you are coming from.

Is this a boot priority setting issue in bios ? For now let's see if you can boot the usb as a liveMedium.
Set in bios to boot the usb drive as 1st boot priority;
Boot the liveUSB,
Can you boot now directly to the boot options screen, and choose "try ubunty " -> desk top ?
Yes ?
Reboot -> boot options screen -> choose "boot from first hard disk" option.

What results ?

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by smcb3357 on 2013-11-03
Greetings, Bashing-om ~ been a busy day. Will test your procedure now and report shortly...

---

### Post by smcb3357 on 2013-11-03
Setting the bios to boot to the live USB works fine. I get the same results whether I press the shift key or not: I get a GNU/Grub screen with three choices: Try Ubuntu with out installing; Install Ubuntu; or Check Disk for Defects.

---

### Post by smcb3357 on 2013-11-03
Then it boots to the live USB just fine.

---

### Post by Bashing-om on 2013-11-03
smcb3357;

Not at all as I expected.
I have not used a liveUSB, however, the procedure should be the same as in a liveDVD.
Try again from a cold boot.
As soon as the bios screen clears, depress -and hold -the left shift key ->language screen, escape key to accept the default, ->boot options screen (???)
We do need to get you booting the liveUSB to rule out hardware issues and to work from a known installation medium.

[INDENT][INDENT]try try again
[/INDENT][/INDENT]

---

### Post by smcb3357 on 2013-11-03
OK ~ I turned off the machine. Turned it on and pressed the left shift key (first time that anyone has mentioned 'left'). I get the same result: I get a GNU/Grub screen with three choices: Try Ubuntu with out installing; Install Ubuntu; or Check Disk for Defects.

It is my understanding that selecting Try Ubuntu is booting to the live USB

---

### Post by Bashing-om on 2013-11-03
smcb3357; Yeah.

That mode is the live mode .. 

What we need here is the means to affect the booting into that live mode. Here as I understand it if you boot with "try ubuntu" you are also going to a black screen, the same as in the actual install.

If we can get you to that liveUSB boot options screen and set an option as "nomodeset" that sets vesa as the driver .. that is pretty uniform and almost certain to boot to the GUI if one has Nvidia or ATI graphics cards - and not switchable.

Like I have advised, I have not used a USB to boot from, I had expected the ability to boot to the boot options screen to exist also in the USB medium.

I going to go see what I can find out about this sloppyation.

[INDENT][INDENT]i will be back
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-11-03
smcb3357; I am back !

Near as I can find out, at the boot options screen; try ubuntu ect ect -> f6 key should activate the boot options.

And also, while it is on my mind .. is secure boot an issue on this machine ? If so, I have seen advisories that Secure Boot should be disabled .

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by smcb3357 on 2013-11-03
Ah ~ when I boot to the USB (Try Ubuntu), I get Ubuntu running from the USB with no problems.

I will try F6 and see what happens.

---

### Post by smcb3357 on 2013-11-03
F6 did not change the boot process. I still get the GNU/Gnome screen with the same three choices.

Secure boot is on this machine and was a problem with Mint (which caused me to change to Ubuntu), but has not been an issue with Ubuntu.

---

### Post by XBNCPRk on 2013-11-03
What version is your built in graphics card? There are several that have aged out of group supported by default. I assume the usb flash drive you are successful from is 12.04. If so, try recreating the usb flash drive using 12.10 as the template and see if you can boot from that as well. This will quickly help you see if its an issue with the included driver or something else.

---

### Post by Bashing-om on 2013-11-04
smcb3357; OK !

As you can boot "try ubuntu" let's try this from the actual install:
Boot the install ubuntu, soon as bios screen clears depress left shift key -> grub menu;
Top most entry highlighted, "e" key for edit mode;
arrow down and across to the term "quiet splash" and enter the term "nomodeset" - with out the quotes;
ctl+x to continue the boot process -> GUI login;
Login, username and password -> desktop, degraded graphics at this point is ok.
We need now to find the Additional Drivers utility.
Version 12.10 launcher -> Software Center ->Software Sources(edit menu option on top task bar) ->Additional Drivers (tab in Software Sources) [must have 'net connectivity ]//assumes that 3rd party software sources have been enabled// Install the recommended driver.

Reboot, now booting to good graphics ?

[INDENT][INDENT]hey, it could happen
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-11-04
smcb3357; 

I am done for this session. I will pick this back up on my morrow,

see ya.

[INDENT][INDENT]cheers
[/INDENT][/INDENT]

---

