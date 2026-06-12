---
title: "cannot boot"
date: 2015-07-23
forum: General Help
---

### Post by jgw on 2015-07-23
I am using ubuntu 14.10   I cannot boot.  

I just updated my computer with synaptic.  First I tried the software updater.  The software updater would go through all its initial stuff and then show a screen offering to update the computer.  Anytime I pushed the button, to update the computer, the software updater would simply go away (I would then get the send report screen).  I checked the details but all that said was the location, and name. of the software updater.  Then I decided to goto synaptic, mark any updates and then run them.  That seemed to work just fine.  Then I thought I would take another run at the software updater and a box came up telling me I had to restart the computer after the update.  I then tried to restart the computer.  the computer gets to the screen with "ubuntu 14.10" and the 4 little dots.  Its stuck there.  If I reset I will then get the screen with options for ubuntu, advanced, and a couple of memory tests.  I suspect if I made the right choice I could move along but have no idea what the right choice might be.  I also have a ver 14.10 cd which I could use but I thought I should, first, lay all this out and get some advice.

Thank you................

---

### Post by pissedoffdude on 2015-07-23
Hi,

Can you boot into recovery mode from the grub menu (just press a few keys to get to it if Ubuntu's the only OS on your computer)?  See if you could boot into that or if not, let us know which stage it hangs on since it goes into verbose mode.  I'd upgrade all the software at that point and try again, but we should get some info from there.  If not, you can enable verbose booting from there and then let us know what issues you face afterwards.

---

### Post by jgw on 2015-07-23
thanks for the reply.

I can boot into recovery mode (advanced settings).  I then have the option of ubuntu, with linux 3.16.0-44 (generic or generic (recovery mode) to ubuntu, with linux 3.16.0-28-generic or generic (recovery mode.  Oh GNU GRUB version 2.02~beta2-15ubuntu0.1 is at the top of the screen.

at the bottom of the screen it also says to enter to boot the selectd OS, 'e' to edit the commands before booting, or 'c' for a command-line, ESC to return previous menu.

I have no idea how to enable verbose booting.
menu (filesystem state: read-only)
If I choose recovery mode I get to a recovery menu.  I have tried clean, dpkg, fsck and grub to no avail.  
I can get to the root shell prompt

Oh, then I started a boot and I was in visual mode and it was stopped because it could not find a drive.  I had removed that drive and replaced it with another.  I cannot figure out how to remove the drive from /media/.  It does not show up in disks.  When I right click on it 'delete' is greyed out.  I am, however, currently booted up.  This is all mysterious.....

I opened the folder, in media, as root, and deleted it.  I think I have fixed my problem but am not sure.  Tomorrow I will have at it again and see if I can now boot.


thoughts?

---

### Post by pissedoffdude on 2015-07-23
Are you able to run a 'sudo update-grub' after booting into recovery mode? It sounds like it can't locate the drive to boot, because it was replaced.  See if you can re-load the boot configuration with that command in recovery mode

---

### Post by Bucky Ball on 2015-07-24
The update would have been unsuccessful as 14.10 reached end-of-life yesterday and the repositories possibly no longer exist. That's why your updater is doing nothing. All over for 14.10, move on, nothing to see here. There will be no further updates or upgrades.

I suggest you boot from Live media, backup valuable data and install a supported release, 14.04 LTS supported until 2019 or 15.04, supported until January 2016. You can also upgrade via the net but if you have a broken system, not a good idea. If you do go that way switch off all manually installed PPAs prior to the release upgrade.

---

### Post by jgw on 2015-07-24
Bucky;
Thanks for the response.  Just wanted you to know that I copied your response and created a new post in the update section as your response has caused me to have yet more questions that were off this subject.

---

