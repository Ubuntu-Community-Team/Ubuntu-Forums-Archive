---
title: "System is booting up. See pam_nologin(8). I can not login into Ubuntu in any"
date: 2016-06-09
forum: General Help
---

### Post by Sherman_Willden on 2016-06-09
I am completely locked out. I can not enter my password as the word Retry exists there and the message above it states "System is booting up. See pam_nologin(8) .. So how do I get into Ubuntu without reloading it?

Thank you;

Sherman

Here is more information. I am dual Win7-Ubuntu boot with Ubuntu 16 installed which I upgraded from 15.4.

I do not know why but I can now log back into the Ubuntu side. I rebooted from Ubuntu three times with the same System is booting up problem. I went to Win7 to post this then I thought I would try again. I am back into the Ubuntu side. Does anyone know what happended?

---

### Post by anders20 on 2016-06-10
I get the same error message sometimes, i'm running Ubuntu Server 16.04 
When i manually reboot, I get in without the error message. Anyone have a fix for this?

---

### Post by asgard2 on 2016-06-10
I have the same problem until today, reboot fixed this for now. But why ...?
win7 Dual Boot is installed.

---

### Post by anders20 on 2016-06-11
Anyone know why? For now a manually reboot fix it, but i can't keep doing that all the time...

---

### Post by QkiZ on 2016-06-12
I have same issue. I think that is related to last update of console-setup-linux, console-setup and keyboard-configuration to version 1.108ubuntu15.1. I made downgrade to earlier version and testing now.

---

### Post by Fluxflixflex on 2016-06-12
same issue here, a reboot is necessary, Ubuntu 16.04.

Thanks

---

### Post by anders20 on 2016-06-12
May we see a Ubuntu dude tell us how to fix it, or that they know about it and they are fixing it?

---

### Post by X-RED_Tech on 2016-06-12
> **anders20 said:**
> May we see a Ubuntu dude tell us how to fix it, or that they know about it and they are fixing it?

You're as much a Ubuntu dude as anybody else around here. This isn't a payed tech support. :D
With so little to go on no wonder this thread went the way it did. And already marked as solved and you aren't the OP... I suggest you open your own thread assertively posting Ubuntu release, hardware specs, exact error messages, etc.

---

### Post by ahhyes on 2016-06-14
> **X-RED_Tech said:**
> You're as much a Ubuntu dude as anybody else around here. This isn't a payed tech support. :D
With so little to go on no wonder this thread went the way it did. And already marked as solved and you aren't the OP... I suggest you open your own thread assertively posting Ubuntu release, hardware specs, exact error messages, etc.

This is actually a bug. I've been seeing this myself and it appears I am not alone.

Rebooting is just a workaround that fixes this _sometimes_ and its sheer luck, due to a race condition. The issue seems to be affecting other distro's too and seems to be due to a stale /run/nologin file being left lingering after boot, making login impossible. So its not really solved at all until the underlying race condition (bug) gets fixed.

If you ctrl-alt-f1 and login as root and remove /run/nologin all will be well (for a little while).

Please see the following links where its explained in more detail:

[https://bugzilla.opensuse.org/show_bug.cgi?id=980324](https://bugzilla.opensuse.org/show_bug.cgi?id=980324)

Bug filed with systemd author:

[https://github.com/systemd/systemd/issues/3436](https://github.com/systemd/systemd/issues/3436)

---

### Post by MikeMecanic on 2016-06-14
The only way to get out of there is by pressing CTRL+ALT+F1 and then CTRL+ALT+DELETE.
 
 
 This bug is in Kylin and Ubuntu.  In Kylin, there is no place to enter the password just the message.  On Ubuntu, it’s written retry instead of an empty space for the password.  Both were set to automatic login.
 
 
 Message:  ‘’ System is booting up.  See pam_nologin (8)’’
 
 
 BTW, CRTL+ALT+F1 is not enough because it is not possible to enter our user name and then run sudo reboot.  CTRL+ALT+DELETE is sudo reboot and the bug disappear each time for me.
 
 
 Report this bug a few weeks ago at the [Testing Tracker]("http://iso.qa.ubuntu.com/") website for Kylin.  It was on the first reboot after a fresh install.  Just got the bug after loading the last Kernel update: 4.4.0.25 (Ubuntu xx 20160612).

---

### Post by ahhyes on 2016-06-14
> **MikeMecanic said:**
> 
 Message:  &#8216;&#8217; System is booting up.  See pam_nologin (8)&#8217;&#8217;
 
 
 BTW, CRTL+ALT+F1 is not enough because it is not possible to enter our user name and then run sudo reboot.  CTRL+ALT+DELETE is sudo reboot and the bug disappear each time for me.

The only user unaffected when /run/nologin is present, is '**root**' (UID 0), if you have set a password for the **root** user itself, you _can_ CTRL-ALT-F1 and login as **root **(must be root, no other user account will work), then remove the /run/nologin file. If you then switch back to your graphical login, you will be able to login as normal.

---

### Post by MikeMecanic on 2016-06-14
> **ahhyes said:**
> The only user unaffected when /run/nologin is present, is '**root**' (UID 0), if you have set a password for the **root** user itself, you _can_ CTRL-ALT-F1 and login as **root **(must be root, no other user account will work), then remove the /run/nologin file. If you then switch back to your graphical login, you will be able to login as normal.

I should never be there when automatic login is enable with or without a **frozen password pop-up**.
 
 A detail was missing:   
 
 The reason why I click the second time on CTRL+ALT+Delete is because after entering my user name, the tty terminal returns the same message* and it freezes.  I have an admin account only and I'm dual boot with TH_2.

 The good news is that it works also when the monitor goes into a black screen (no video output).  I just have to wait for the boot sequence to complete (when the HDD becomes noise free): CTRL+ALT+F1 a few times and CTRL+ALT+DELETE with no monitor.  The machine will reboot.
 
 
 * &#8216;&#8217; System is booting up. See pam_nologin (8)&#8217;&#8217;

---

### Post by pablosquared on 2016-06-15
I've had the same problem a few times now on 16.04 (only). Rebooting fixes it for a while.

---

### Post by ahhyes on 2016-06-15
> **pablosquared said:**
> I've had the same problem a few times now on 16.04 (only). Rebooting fixes it for a while.

Rebooting fixes it only because sometimes the race condition doesnt occur and /run/nologin gets removed at the end of startup. I've explained the cause a couple of posts above.

This is a bug 100% and the fingers are being pointed at systemd from what I can tell.

might be worth opening a bug for ubuntu if someone hasnt already?

---

### Post by Glasairman on 2016-06-17
> **ahhyes said:**
> Rebooting fixes it only because sometimes the race condition doesnt occur and /run/nologin gets removed at the end of startup. I've explained the cause a couple of posts above.

This is a bug 100% and the fingers are being pointed at systemd from what I can tell.

might be worth opening a bug for ubuntu if someone hasnt already?

This has happened to me several times in the last few days - and usually was cured by 1 -3 reboots, but not this time. 

So I looked at the logs with ***journalctl -xb*** and noticed file corruption in my /home which is a separate HDD in my laptop.  I then ran ***fsck -f  /dev/sdb1*** to fix, and rebooted. This time it went well.

---

