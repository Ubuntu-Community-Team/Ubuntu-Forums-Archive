---
title: "Unable to change forgotten password"
date: 2020-07-26
forum: General Help
---

### Post by project-uwb on 2020-07-26
Hi Community, I am a new ubuntu user and had an old Toshiba laptop which I used to install Ubuntu 16.04 LTS a couple of years ago. Fast forward to today and I have obviously forgotten the password. I searched on youtube and found the following video [https://www.youtube.com/watch?v=YE-HTRoFr4o](https://www.youtube.com/watch?v=YE-HTRoFr4o) Followed it and was able to get to the single user login. Once I was at the command prompt, I typed "passwd <username>" and received the message similar to "User not valid" or "User not available". I used the exact user id as per the log in screen and not sure why this error. After this I tried "passwd" without any user name after the command and I was able to reset the password, got the message "Password change successful". I then restarted the computer and tried the new password but it doesnt work! Now I am locked out of this computer and really need to set it up for online learning. Could anyone help please! Thanks.

Edit 27-07-20: Ok, I figured out that I did not make a bootable USB and hence had the issue with booting from USB. All resolved, I am not installing Ubuntu 20.04 and hopefully its all resolved. Thanks everyone!

---

### Post by TheFu on 2020-07-26
If you haven't used it in a few years, time to upgrade.  Get a 20.04 desktop flavor and [B]do a fresh install.
[/B]I didn't watch video. Sorry.

What I think happened depends on the way you got a 'single user login'. There are a few ways to accomplish this.
[LIST]
[*]Use grub boot options
[*]Use recovery mode (hidden in Advanced Options on the Grub menu)
[*]Use a Try Ubuntu "Live" installer source
[/LIST]

In single user mode, you are logged in as 'root'.  Running **passwd** with no options will change the root password. That worked in the environment you were in. Since Ubuntu systems don't use root accounts directly, that isn't exactly useful.

The other methods would have you logged in a "ubuntu" probably.  Whenever a userid runs 'passwd' without options, that means to change that userid's password.  Changing 'ubuntu' the userid's password isn't exactly helpful, since an installed system wouldn't have that account. Again, this would change the password only in the "live boot" environment, which isn't exactly useful.

There is a thing called a "chroot environment". To modify the password for an account on an already installed system, while booted from a **Try Ubuntu** disc/flash drive, you'd need to setup a chroot environment.  It isn't THAT hard, but for someone new, getting all the commands exactly correct will be difficult. Any typo and it won't work.  Miss one of the 8 commands and it won't work.

There are a few other techniques to get root on the system, but you'll need some admin skills to get there.  A competent admin with physical access to any system can gain access, unless whole disk encryption was setup. If encryption was used, almost everyone should just give up. The only way to hack into an encrypted system is to trick someone who knows how to unlock the storage into providing that information. Since you would be that person and don't know it, time to wipe and start over.

In June, I needed to fix a boot problem with a Ubuntu 20.04 system. Somehow all the kernels had been removed during patching. No idea how that happened - even today.  I used a Try Ubuntu environment + chroot to get a running system and installed a kernel. It was a hassle.  I do backups really well. Daily, automatic, versioned.  Had backups for that system.  I should have just done a fresh install and restored files from backups. It would have been faster; about 30 min wall time and about 5 minutes of my hands-on time.

For someone with limited Unix knowledge and nearly zero Ubuntu skills, **the easy answer is to perform a fresh install.** That should take about 10-15 minutes.  After all, if the system hasn't been used in years, it is way out of date and updating it will probably take much longer than a fresh install.

---

### Post by pbear42 on 2020-07-26
Out of curiosity, I watched the video.  The method given is correct.  At a guess, the username you recall clearly isn't in fact correct.  There are ways to fix this, but they're pretty complicated for a newbie.  As **TheFu** says, would be easier (even faster) to reinstall.

By the way, I understand the appeal of videos.  We're a verbal species.  The information density of videos, though, is very low.  Also, there's no quality control.  Learn how to do this with manuals, help pages, etc. from solid sources.  You'll learn more and it's easier to refer back.  By contrast, finding a particular tip in a video is like searching for a needle in a haystack.

---

### Post by TheFu on 2020-07-26
As pbear42 says, I like how-to videos too, provided I'm able to follow along with each detail and reproduce every step correctly.  It is easy to miss subtle things in videos. I have.  Think of videos as an overview, so we know what we're getting into.  Sometimes the video will have me seeking another solution or just walking away with a "that's too hard for me."  

I have 3 important home projects now where the videos have me scared.  But these are HW, not software, projects. The current hardware, mostly works and 1 non-trivial part needs a complex replacement.

---

### Post by ajgreeny on 2020-07-26
Many years ago I had to use the method shown in the page at [https://www.psychocats.net/ubuntu/resetpassword](https://www.psychocats.net/ubuntu/resetpassword) but I am not certain this still works as it used to.

Worth a try I think to see if that does still work for you, but make sure you use the remount command ***mount -o rw,remount /*** after booting into the root console to remount the root partition as read/write or it will not work as no changes will be made.

---

### Post by project-uwb on 2020-07-27
Thanks to everyone that replied and provided suggestions.

Hi TheFu, thanks for your explanation. I understand what you say with regards to changing password in the working environment. After I posted this message, the next thing I did was to try and install 20.04. So my setup is a Toshiba laptop which had Widows 7. I wiped the windows and installed the Ubuntu 16.04 as mentioned a couple of years ago. So the only OS on the laptop now is Ubuntu 16.04. I got the official ISO file on a USB and changed the BIOS setting to boot from USB as the first option. The first time I tried to do this, I got a message saying that "No operating system was found on the USB". I retried a couple of time had the same message. After this I also tried all 3 USB ports on the laptop and still was not able to boot from USB. This time the message changed to "PXE-E61: Media test failure, check cable" & "PXE-MOF: Exiting PXE ROM". Not sure what these messages mean but sounds like I may have a hardware issue which is not allowing the laptop to boot from USB.

 So I assume there is no other way for me other than trying to change the password from root access. I am willing to take the risk and follow instructions if these are documented. Could you please let me know if the instructions are documented on how to access the "chroot environment" and change the password? Thanks again!

Also anyone from the community if you know how to get past the error or change password, please reply and advise. Thanks!

Edit 27-07-20: Ok, I figured out that I did not make a bootable USB and hence had the issue with booting from USB. All resolved, I am not installing Ubuntu 20.04 and hopefully its all resolved. Thanks everyone!

---

### Post by deadflowr on 2020-07-27
PXE is a boot method allowing booting from a networked server. It's actually pretty cool.
Usually it's a boot option in the BIOS typically set second or third in order of what's available to boot.
(ie, if the first boot option is set to usb but no usb device is available, it sets to try and boot the second boot option.
If the second boot option is also not available it sets to try booting from the third option, and so on)

That said,
How did you install 16.04 on it originally?
How did you put the new install ISO on the usb?
Did you follow any guides or use any specific programs to do so?

---

### Post by TheFu on 2020-07-27
> **project-uwb said:**
>  
Edit 27-07-20: Ok, I figured out that I did not make a bootable USB and hence had the issue with booting from USB. All resolved, I am not installing Ubuntu 20.04 and hopefully its all resolved. Thanks everyone!

That is a confusing paragraph. Seems a "NOT" is added or missing?

IF this really is fixed, please take the time to help the community by using the "Thread Tools" button near the top to make it "SOLVED".

---

### Post by pbear42 on 2020-07-27
Pretty sure it's a typo, i.e., supposed to be "I am *now* installing ... "

---

### Post by pbear42 on 2020-07-27
> **ajgreeny said:**
> ... make sure you use the remount command ***mount -o rw,remount /*** after booting into the root console ... 
I realize the linked tutorial says this, and don't doubt it was true at some point, but it's no longer true.  Just confirmed in both Ubuntu 18.04 and 20.04.  Can't test 16.04, as I culled that VM when I installed 20.04, but did test Mint 18.x (which was based on 16.04) and that worked without remount also.

Don't take my word for it, of course.  Very easy to test, then revert.

---

