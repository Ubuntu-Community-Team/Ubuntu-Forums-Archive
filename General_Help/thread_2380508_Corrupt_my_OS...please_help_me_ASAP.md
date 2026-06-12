---
title: "Corrupt my OS...please help me ASAP"
date: 2017-12-18
forum: General Help
---

### Post by shadowstorm56 on 2017-12-18
So long story short I went to upgrade from 14 to 16... the result is now the OS will not boot in any mode not even rescue mode and IDK what to do...that OS has my website on it which uses a SQL database so yes I could reinstall the OS and the site but it is very hard to get SQL to transfer over.... So I really need help to fix the install so I can have my website up and running again. It is the standard kernal panic error that freezes after the grub menu and then stops there... please help. I am not sure if I can run somthing from the command line in grub but if there is I don't know the command to do it.

---

### Post by ian-weisser on 2017-12-18
Since you can reach the GRUB menu, try booting from an older kernel in GRUB.

---

### Post by shadowstorm56 on 2017-12-18
> **ian-weisser said:**
> Since you can reach the GRUB menu, try booting from an older kernel in GRUB.

I tried multiple options of that with no change.

---

### Post by ian-weisser on 2017-12-18
Let us know when you have tired *all* the older kernels in GRUB.
Your system used to boot from those, no reason that should change.
If *every* kernel in your GRUB panics (very, very rare), then a reinstall may be your best option.

I think you have just learned a very important lesson about backups.
If you decide to reinstall, use a LiveUSB to salvage all your data first. It's a bit tedious...but much less so that losing your data permanently.

---

### Post by shadowstorm56 on 2017-12-18
I also learned never to do ubuntu updates... apparently there trash. It can't be that screwed... how can running an update break a system beyond repair.. all I want is my website.. all I can't get is my website. I tried the oldest one and the second newest sofar tbh.

---

### Post by shadowstorm56 on 2017-12-18
> **ian-weisser said:**
> Let us know when you have tired *all* the older kernels in GRUB.
Your system used to boot from those, no reason that should change.
If *every* kernel in your GRUB panics (very, very rare), then a reinstall may be your best option.

I think you have just learned a very important lesson about backups.
If you decide to reinstall, use a LiveUSB to salvage all your data first. It's a bit tedious...but much less so that losing your data permanently.

I hate problems like this...

---

### Post by ajgreeny on 2017-12-18
> **shadowstorm56 said:**
> I hate problems like this...
We all hate problems like that which is why we all make sure we prepare before such a major process.

Backups should always be available for your important personal files and configurations that would be lost if the computer completely crashed.
> **shadowstorm56 said:**
> I also learned never to do ubuntu updates... apparently they're trash.
No they are not; a large number of users manage them effectively, but always after preparation, just in case.

---

### Post by shadowstorm56 on 2017-12-18
> **ajgreeny said:**
> We all hate problems like that which is why we all make sure we prepare before such a major process.

Backups should always be available for your important personal files and configurations that would be lost if the computer completely crashed.

No they are not; a large number of users manage them effectively, but always after preparation, just in case.

Obviously that was just an irritated comment of mine lol... Must be some solution though

---

### Post by The Cog on 2017-12-18
You could perhaps use a live CD, mount the website drive and copy the website contents and other stuff off to an external drive. Then reinstall, then copy the data back onto the new system. That is of course assuming that it is possible to mount the website drive - a corrupt drive might be the cause of the kernel panic.

---

### Post by shadowstorm56 on 2017-12-18
> **ian-weisser said:**
> Let us know when you have tired *all* the older kernels in GRUB.
Your system used to boot from those, no reason that should change.
If *every* kernel in your GRUB panics (very, very rare), then a reinstall may be your best option.

I think you have just learned a very important lesson about backups.
If you decide to reinstall, use a LiveUSB to salvage all your data first. It's a bit tedious...but much less so that losing your data permanently.

All of them panic...... also I can only reinstall if I can retrieve the site, there has to be a person who can fix the os, well help me Fix it... I'm not rebuilding an entire website. I would never have updated to 16 if I knew it would cause a horrible fail.

---

### Post by ajgreeny on 2017-12-18
You could also try running fsck from the live system on each ext# partition of your old installation in the hope, if corrupt, and not just throwing a wobbly after a version upgrade, that repairs any corruption and allows you to at least save the files you need.

From the live system use command ```
sudo e2fsck /dev/sda#
``` to see if that gives you any information or reports problems.

---

### Post by yancek on 2017-12-18
Was this upgrade from the LTS 14.04 to 16.04?
Did you see any error or warning messages during the upgrade?
Did the upgrade finish successfully?
Can we safely assume that Ubuntu is the only operating system?
If you still have an Ubuntu Live DVD or flash drive, you could boot that and go to the site below and add the boot repair :ppa as explained.  After installing it, run it by selecting the option to Create BootInfo Summary.  This will give you a link that you can post here for others to review as it will show a lot of information on your system and boot files.  Make sure you do not try to repair, just post the link.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by shadowstorm56 on 2017-12-18
> **ajgreeny said:**
> You could also try running fsck from the live system on each ext# partition of your old installation in the hope, if corrupt, and not just throwing a wobbly after a version upgrade, that repairs any corruption and allows you to at least save the files you need.

From the live system use command ```
sudo e2fsck /dev/sda#
``` to see if that gives you any information or reports problems.

I will try that, all  I care about is the website. There were a few errors during the update but none that were major. First time after the update it booted to Login but would not login just refreshed the login page each time I tried. I was told that trying to get a database based site working after a transfer is nearly impossible so thus why I'm trying to see if I can fix the install. I wish I could copy paste the errors on boot but all I could do is take a picture.

---

### Post by ajgreeny on 2017-12-18
I hope that you are aware that you must replace the **sda#** in my command with the partition number, eg, **sda1**, if that was your root partition.

Sorry for any confusion I may have caused.

---

### Post by shadowstorm56 on 2017-12-18
[http://paste.ubuntu.com/26211830/](http://paste.ubuntu.com/26211830/) this is the report from boot repair. Also to the other guy it said somthing about a missing magic number?

---

### Post by shadowstorm56 on 2017-12-18
> **ajgreeny said:**
> I hope that you are aware that you must replace the **sda#** in my command with the partition number, eg, **sda1**, if that was your root partition.

Sorry for any confusion I may have caused.

Forgot to quote

---

### Post by ian-weisser on 2017-12-18
> **shadowstorm56 said:**
> There were a few errors during the update but none that were major. First time after the update it booted to Login but would not login just refreshed the login page each time I tried.

That's a desktop crash. There are a couple common reasons for those, most are easy to fix.
How did you get from desktop-crash to all-kernels-panic?

Understanding what you intended (and what you actually did) will enable us to offer better advice.

---

### Post by shadowstorm56 on 2017-12-18
> **ian-weisser said:**
> That's a desktop crash. There are a couple common reasons for those, most are easy to fix.
How did you get from desktop-crash to all-kernels-panic?

Understanding what you intended (and what you actually did) will enable us to offer better advice.

It told me I should upgrade to 16... so I did... part way through the process it restarted and here I am
After alot of struggling and use of boot repair I got it to boot in 1 kernel mode but it is weird... It says the kernel name and then systemd after it. But it's really messed up and so is my site... it's like it gliched out part way through the upgrade.

---

### Post by yancek on 2017-12-19
Your boot repair output shows that you have 3 hard drives, the first two (sda and sdb) are windows only and the 3rd (sdc) shows a windows partition (sdc2) and Linux (sdc4).  sdc2 shows vista, is that just a data partition or an actual vista OS?  sdc4 is your Ubuntu install and your boot files look good pointing to the right partition with the correct UUID.  The problem I see is that the only drive which has Grub code in the MBR is sda, apparently pointing to the Ubuntu files (sdc4).  I also notice that sdc is a GPT partitioned drive and the other 2 drives are MBR, labelled msdos which is not the norm.  Not sure how that happened or if it was like that before.  You might see if you can find an Advanced option in boot repair to install Grub to the MBR of sdc (your 1.8TB drive).  If you note at the bottom of the boot repair, it suggests re-installing Grub but would do it for all 3 drives which isn't really necessary.  If you can do this, make sure you change the BIOS to boot from sdc before trying to re-boot.

Other members have suggested that you might try copying your server (/var/www?) files to another drive and copying them back later after a new install if that is necessary.  When you boot your Live DVD or flash drive, can you mount and access sdc4 to test to see if it is even accessible.

---

### Post by ian-weisser on 2017-12-19
> **shadowstorm56 said:**
> part way through the process it restarted
That's unusual.
Any ideas why your system restarted before a release-upgrade was complete?
It shouldn't do that. I've only see that happen on defective hardware.

> **shadowstorm56 said:**
> I got it to boot in 1 kernel mode but it is weird... It says the kernel name and then systemd after it. But it's really messed up and so is my site... it's like it gliched out part way through the upgrade.
Hmmm. That's a bit too vague for us to help.


Have you backed up your data?
Strongly recommended.

---

### Post by shadowstorm56 on 2017-12-19
It's accessible yes and it needed to restart to do something in the upgrade it warned me. But it uses a database so the website may be lost. Oh the fun

---

### Post by dragonfly41 on 2017-12-19
Provided that you have exhausted all ideas suggested above, using Ubuntu LiveUSB to recover your MySQL data, and you have no backups, there is a "last chance saloon" option you might try.   But caveat .. staying with Ubuntu LiveUSB recovery is by far the best option.   Personally I would buy a new drive + container and use your failed drive as a USB external drive to recover.

Here is the option ...

If you can still boot into Windows .. you can download R-Linux (free) to run in Windows.

[http://r-tt.com](http://r-tt.com)    Download and install R-Linux 5.5

Create a folder to receive recovered Linux files.

e.g. C:\Users\yourusername\R-Linux Recovery\ .. but it can be anywhere.

Run R-Linux and look for your Ubuntu partition.

Your MySQL files will be found in 
/var/lib/mysql
/etc/mysql

Recover files (this might take a long time to index files, possibly a couple of hours).

Only select the marked (ticked) file paths you are interested in such as above.

Recover into target folder in Windows you first created above.

Later move these recovered files into a drive to be read by a fresh installation of Ubuntu.
Check correct permissions to set.

---

### Post by ian-weisser on 2017-12-19
EDIT: dragonfly41 said it better

---

### Post by yancek on 2017-12-19
Have you checked the Advanced options on boot repair?  I don't have it available to check but you should be able to install Grub to the MBR of sdc as recommended in the boot repair to see if that helps.

---

