---
title: "Download problems"
date: 2007-04-20
forum: General Help
---

### Post by xluix on 2007-04-20
I´m trying to download Wubi but it´s impossible.
The download process stop (photo) and nothing more.
Help please

---

### Post by ago on 2007-04-20
All old ISO files (including beta) were removed from Ubuntu servers worldwide to prepare for the feisty final release. Moreover the servers are quite overloaded. Not sure if and when the situation will be restored. Anyway you can expect a wubi minefield that supports feisty final in a couple of days, I would suggest to wait untill then.

---

### Post by Yubimusubi on 2007-04-21
There is a way; I just got it to work.  It's just a bit more difficult.

Install like normal, then when it has a problem downloading, open C:\wubi\config.ini in [insert favorite text editor here].  Set the following lines to look like this:

isolocation=http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso.torrent
isoname=ubuntu-7.04-alternate-i386.iso
ddlisolocation=http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso

Then either delete or comment out (prepend a # symbol) the line that starts "ddlsha1"

Hope this helps someone out there.

EDIT: I may have spoken too soon.  The iso successfully downloaded but it failed when I rebooted, giving me only a busybox shell.  It may have something to do with the fact I'm running a 64-bit processor but I doubt it.  Any one else care to give it a shot?

---

### Post by fimp on 2007-04-21
> **Yubimusubi said:**
> There is a way; I just got it to work.  It's just a bit more difficult.

Install like normal, then when it has a problem downloading, open C:\wubi\config.ini in [insert favorite text editor here].  Set the following lines to look like this:

isolocation=http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso.torrent
isoname=ubuntu-7.04-alternate-i386.iso
ddlisolocation=http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso

Then either delete or comment out (prepend a # symbol) the line that starts "ddlsha1"

Hope this helps someone out there.

EDIT: I may have spoken too soon.  The iso successfully downloaded but it failed when I rebooted, giving me only a busybox shell.  It may have something to do with the fact I'm running a 64-bit processor but I doubt it.  Any one else care to give it a shot?
I tried it but got a Disk not found error when booting.

---

### Post by ecology2007 on 2007-04-21
> **Yubimusubi said:**
> There is a way; I just got it to work.  It's just a bit more difficult.

Install like normal, then when it has a problem downloading, open C:\wubi\config.ini in [insert favorite text editor here].  Set the following lines to look like this:

isolocation=http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso.torrent
isoname=ubuntu-7.04-alternate-i386.iso
ddlisolocation=http://releases.ubuntu.com/feisty/ubuntu-7.04-alternate-i386.iso

Then either delete or comment out (prepend a # symbol) the line that starts "ddlsha1"

Hope this helps someone out there.

EDIT: I may have spoken too soon.  The iso successfully downloaded but it failed when I rebooted, giving me only a busybox shell.  It may have something to do with the fact I'm running a 64-bit processor but I doubt it.  Any one else care to give it a shot?

Nice try but it will not work.
Kernel version of wubi-beta-v3.exe is 2.6.20-12.
Kernel version of ubuntu-7.04-alternate.iso  is 2.6.20-15.
The debian installer will not start.

---

### Post by tuxcantfly on 2007-04-22
try the new wubi-7.04-v1, it should download properly; it's now using the final released feisty isos

---

### Post by xluix on 2007-04-22
> **tuxcantfly said:**
> try the new wubi-7.04-v1, it should download properly; it's now using the final released feisty isos

Thank you very much.
Now another problem with wifi, i have a broadcom and no wireless.

---

### Post by fimp on 2007-04-22
> **tuxcantfly said:**
> try the new wubi-7.04-v1, it should download properly; it's now using the final released feisty isos
It downloads but when I boot it says:

  Booting 'Ubuntu'

find --set-root /wubi/boot/menu.lst

Error 17: File not found

Press any key to continue...




If I do press any key it just repeats itself.

---

### Post by fimp on 2007-04-22
Crap! Now when it is about to load the windows bootloader, it says:

Error 25: Disk read error


I guess Wubi isn't that safe yet...
Can you help me restore the Windows bootloader?

---

### Post by hamishau on 2007-04-23
xluix,

to get broadcom wireless to work look here: [http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102)

it works perfectly!

however, you may need to change your ethX to "roaming mode" to pick up an IP address

enjoy :-)

hamish

---

### Post by ecology2007 on 2007-04-25
> **fimp said:**
> Crap! Now when it is about to load the windows bootloader, it says:

Error 25: Disk read error


> I guess Wubi isn't that safe yet...
Can you help me restore the Windows bootloader?

Run uninstall.exe in wubi folder.

---

