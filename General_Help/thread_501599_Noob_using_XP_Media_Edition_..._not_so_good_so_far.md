---
title: "Noob using XP Media Edition ... not so good so far!"
date: 2007-07-15
forum: General Help
---

### Post by Ken Jacobs on 2007-07-15
I just installed V7.04.03 on my Dell 9100 on a machine that runs XP Media Center Edition. I have plenty of space.

After rebooting and choosing Ubuntu, I get a number of errors. First 6 errors with number -110. Appears to be some problem recognizing USB devices. The first four such errors save something like dev.description read /64. The remaining two of the six errors say something about "device not accepting script", and give addresses 13 and 14. Sorry I don't have the exact errors, as I don't know how to cut and paste into a file I can later reference.

Then I get a message like this

check root = bootarg cat /proc/cmdline ... or missing modules ... devices
cat /proc/modukles ls /dev
ALERT! Does not exist! Dropping to shell.

Busy box ... built-in shell.

To me, a Windows user, and a complete noob to Linux, I am LOST.

I had hoped to see GNOME or some other Windows-line desktop.

Can anyone help?

Thanks!

Ken

---

### Post by ago on 2007-07-15
remove any USB device if you have any plugged in and reinstall

---

### Post by Ken Jacobs on 2007-07-15
Well, booting up (not reinstalling) after detaching all USB devices eliminated the errors about USB devices.  No real surprise there!  ;-)

I still, however, am getting the messages about missing modules, etc.  On booting, and choosing Ubuntu, I get some messages about the disk drives, then NO RAID DISKS ... and a very long pause.  Eventually I get the message about check root=bootarg cat proc/cmdline, etc.

I did cat the file /proc/cmdline, which contains just one line: find=wubi/boot/linux quiet ro

I also tried cat /proc/modules, but it produced a lot of meaningless (to me) stuff, and I could not capture it all.  I tried to use the "more' command to see it in bits, but the vertical bar command (pipe?) | displays as some other character when booting Ubuntu, though not in Windows.   I don't know how to access the content of that file from Windows and post it here, either.

Still no GUI.  So, I'm still stuck.   

Thanks

Ken

---

### Post by ago on 2007-07-15
Do a proper reinstallation. If you still get stacked, see the logs in the /tmp/ folder and attach here the content (you can use the "more" command to read files or copy them to the windows drive "cp /tmp/* /media/host")

---

### Post by Ken Jacobs on 2007-07-15
It takes soooooo long to re-download that I'm reluctant to start all over at that point again.  Besides, what's been downloaded shouldn't be affected by whether or not there are attached USB devices, should it?   Is there a way I can re-install without re-downloading?   Does it matter if the USB devices are connected or not during the install?  Do you have a theory why reinstalling will help?

Thanks

Ken

---

### Post by ago on 2007-07-15
> **Ken Jacobs said:**
> It takes soooooo long to re-download that I'm reluctant to start all over at that point again.

When you uninstall you are given the option to backup the ISO. The backed up ISO will be reused automatically (provided you select the same distro).  Moreover if the download is slow, you can download the ALTERNATE ISO with the download manager/p2p of your choice and place it in the same folder as wubi.

> Besides, what's been downloaded shouldn't be affected by whether or not there are attached USB devices, should it?
If the installation is interrupted it must be restarted from scratch

> Does it matter if the USB devices are connected or not during the install?
In theory not, but we had a couple of people that had issues with that, since disconnecting them does no harm, do so. You can also try both ways and give me some feedback... ;)

> Do you have a theory why reinstalling will help?
Because some files are deleted as soon as installation starts for safety/security reasons, and when you try to run Ubuntu when the installation was not finished, the installer cannot proceed properly

---

### Post by Ken Jacobs on 2007-07-15
> The backed up ISO will be reused automatically (provided you select the same distro).

I did select the option to backup the ISO. and it was created in Wub-save.

> Moreover if the download is slow, you can download the ALTERNATE ISO with the download manager/p2p of your choice and place it in the same folder as wubi. 
Where would I get the ALTERNATE ISO?  And is it any smaller than the original?



Now, though, having de-installed, I don't know how to reinstall!   Sorry to be asking such apparently stupid questions, but I really need more help here.

After the uninstall, the following files exist in Wubi-save: ubuntu-7.04-alternate-i386.iso and home.virtual.disk.  The original directory into which I downloaded Wubi is GONE.   I re-downloaded the installer (Wubi-7.04.04.exe) and when I run it, it doesn't give me an option to start with the ISO.

Am I supposed to burn the ISO to a CD or something?

Thanks for your help.

---

### Post by ago on 2007-07-15
> **Ken Jacobs said:**
> I did select the option to backup the ISO. and it was created in Wub-save.
correct, when you install again, it will scan for a wubi-save folder

> Where would I get the ALTERNATE ISO?  And is it any smaller than the original?
ubuntu/kubuntu/xubuntu/edubuntu website, look for "other download options"

> 
Now, though, having de-installed, I don't know how to reinstall!
run wubi again

> and home.virtual.disk.
delete home.virtual.disk

> The original directory into which I downloaded Wubi is GONE.   I re-downloaded the installer (Wubi-7.04.04.exe) and when I run it, it doesn't give me an option to start with the ISO.
just select the same distro (I assume wubi) and it will find the ISO inside wubi-save.

> Am I supposed to burn the ISO to a CD or something?
nope

---

