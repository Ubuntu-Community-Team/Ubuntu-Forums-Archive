---
title: "Installation failed, root file system error"
date: 2008-04-09
forum: General Help
---

### Post by CAMM on 2008-04-09
I am using Wubi 8.04 rev479. Near the end of the install in Ubuntu I receive an “Installation Failure” error and then it forces me to reboot my computer. When Ubuntu starts back up, I receive the error below.

[INDENT]Loop-mounted file systems already present

The selected partition (partition 2 of /var/lib/partman/devices/=dev=sda) already contains the following system images:

/ubuntu/disks/root.disk

Please uninstall these before trying again.
[/INDENT]
After I click OK on this error, I receive another error.

[INDENT]No root file system

No root file system is defined.

Please correct this from the partitioning menu.
[/INDENT]
I have found that if I hit Ctrl + Alt + Backspace that Ubuntu reloads and, so far, seems to work fine after that.  

I tried deleting /ubuntu/disks/root.disk and when starting Ubunto the installation starts over again and I receive the same “Installation Failure” error and then the same process happens as mentioned above.

I have searched the forums and have been unsuccessful finding a solution.

---

### Post by ago on 2008-04-09
uninstall, run wubi again
after selecting ubuntu at reboot press esc and select the verbose mode.

When it fails look for logs in C:\ubuntu\

If they are not there, repeat the steps, and before rebooting after failure you should press ctrl+alt+f2  and run

sh /custom-installation/hooks/failure-command.sh

---

### Post by CAMM on 2008-04-09
Upon reboot I started it in verbose mode.  After failure a zip file was found titled installation-logs which contains multiple log files.  Is there a particular one I should be looking for?

---

### Post by ago on 2008-04-09
just upload the full zip please (note your password hashed might be in there).

---

### Post by CAMM on 2008-04-09
Log files attached.

---

### Post by ago on 2008-04-09
[https://bugs.launchpad.net/wubi/+bug/214211](https://bugs.launchpad.net/wubi/+bug/214211)

---

### Post by cjwatson on 2008-04-09
Sorry about this. Will be fixed with the next ubiquity upload.

---

### Post by mcnater on 2008-04-09
I too am receiving this error.  When will I be able to download a new version with a fix in it?

FYI, I'm running Windows VISTA currently.

Thanks.

Nate

---

### Post by lulu123 on 2008-04-10
after running wubi/ubuntu fine for a couple of days i wanted to switch to the kubuntu version
,by a reinstall rather than just the kubuntu desktop on top of ubuntu. so after uninstalling and reinstalling of wubi i encountered the same problem as CAMM. hope you can sort this out for me as i really started to like this over my windows xp. thanks in advance ;-)

---

### Post by ago on 2008-04-10
That has been fixed it will appear in newer ISOs

---

### Post by lulu123 on 2008-04-10
just reinstalled wubi and the problem still persists. can you let me know of the new iso and how to go about installing it. hope its as easy as wubi, since i'm a total beginner.

---

### Post by ago on 2008-04-10
[http://cdimage.ubuntu.com/daily-live/current/hardy-desktop-i386.manifest](http://cdimage.ubuntu.com/daily-live/current/hardy-desktop-i386.manifest)

when ubiquity turns 1.8.3 the ISO will contain the fix

---

### Post by lulu123 on 2008-04-10
how long will this take?
in the meantime, should i uninstall the wubi on on my pc?

---

### Post by ago on 2008-04-10
Not sure, could be up to 24 hours, sometimes seeds are blocked by some projects and it may take longer.

---

### Post by lulu123 on 2008-04-10
ok.
so weird, managed to get into ubuntu by pressing ctrl+alt+backspace after the error prompt. but there appeared no login/pass page. is there a way to fix this from within ubuntu. i am in it right now. 
....and back in xp. ubuntu was running slow , eating up all my pcs resources :-(

---

### Post by ago on 2008-04-10
I'd wait for the ISO with the fix.

---

### Post by lulu123 on 2008-04-10
ok.
when it's out, how do i go along installing it? 
same automatic process as wubi or do i need to burn it to a cd and boot it from there ?
thanks for your help

---

### Post by ago on 2008-04-10
As usual, just download the ISO and run wubi in the same folder where you have the ISO. Make sure old ISOs are not around (particularly in /ubuntu-backup)

---

### Post by lulu123 on 2008-04-10
just found this [https://launchpad.net/ubuntu/hardy/+source/ubiquity/1.8.3](https://launchpad.net/ubuntu/hardy/+source/ubiquity/1.8.3)...
would loading thin in ubuntu not fix the error prompt???

---

### Post by ago on 2008-04-10
Yes but the " loading thin in ubuntu " part is not trivial. Much easier to sit and wait a few hours!

---

### Post by lulu123 on 2008-04-10
ok, if you say so.
just cant wait to run it properly again.

---

### Post by ago on 2008-04-10
Well if you are in a rush, you can always use the 8.04 BETA ISO and then upgrade after installation

---

### Post by lulu123 on 2008-04-10
i think i will do that. 
can you help me with installation please.
would downloading the kubuntu version fix this to?
... i thought wubi had installed ubuntu 8.04 beta?

---

### Post by ago on 2008-04-10
Wubi stand alone will download the latest daily ISO, which at the moment is broken.
You have to download manually a BETA DESKTOP ISO (ubuntu/kubuntu/xubuntu) and run wubi from within the same folder

---

### Post by lulu123 on 2008-04-10
ok.
i am downloading kubuntu iso  [http://www.ubuntu.com/testing/hardy/beta](http://www.ubuntu.com/testing/hardy/beta) now.
so will create a folder where i will copy both the wubi.exe and the downloaded iso..
press wubi.exe and it should install, right. will get back to you asap. thanks for the support

---

### Post by lulu123 on 2008-04-10
i got good news. 
the kubuntu iso install via wubi in the same folder went fine. 
no error prompt what so ever and here i am using it already.
thanks a lot for your help

---

### Post by ago on 2008-04-11
The daily ISO has been fixed!

Pleas try it out, make sure you remove the old one!

---

### Post by srikpen on 2008-04-12
I am still facing this issue with the latest rev 482  wubi.

and ubuntu/kubuntu  7.10/8.04 beta version on my m1330
I still get the message "no root filesytem is defined"

How did it work lulu123  ??

---

### Post by ago on 2008-04-12
srikpen please add your installation-log.zip to [https://bugs.launchpad.net/wubi/+bug/216161](https://bugs.launchpad.net/wubi/+bug/216161)

---

### Post by srikpen on 2008-04-16
It seem when using media direct a lot of my friends are facing the same issue.

I will try to upload the logs as soon I try it out soon. will keep you updated.

thanks.

---

### Post by ago on 2008-04-16
Please do a clean uninstall/install
Boot in verbose mode when installing
If it fails post the logs (either in c:\ubuntu\installation-logs.zip under windows, or you will have to zip manually /var/log/ within Ubuntu)

---

### Post by ago on 2008-04-16
Note that if the installation fails (after first reboot). You do have to uninstall and reinstall.

---

### Post by duckdown on 2010-01-20
I am having this error.

I have a computer with a single SATA drive, not RAIDed or anything silly like that.  Has a working XP SP3 installation but trying WUBI with Ubuntu 9.10 boots into "Checking Installation..." then finally says "no root file system is defined" and I just click OK over and over and it does nothing.

I booted into verbose mode, then let it error, and went back to XP.  No .zip file with the logs in c:\ubuntu .

Tried your  ' sh /custom-installation/hooks/failure-command.sh ' and it failed because of all the trailing ^M's on each line..  removed them finally though, here are the logs

---

### Post by djevrek on 2010-04-12
I have same issue when trying to install newest beta ubuntu. It's Ubuntu 10.04 beta 2. Same problem on work and at home.

---

