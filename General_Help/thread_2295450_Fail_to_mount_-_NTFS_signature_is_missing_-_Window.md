---
title: "Fail to mount - NTFS signature is missing - Windows is hibernated, refused to mount."
date: 2015-09-18
forum: General Help
---

### Post by frank105 on 2015-09-18
Hi and thanks in advance for your help.


HQ sent me a new windows laptop. So I am trying to copy a TON of data off of the old one and onto a new laptop. I thought = easy just pull the hard drive and drop into an external drive case to usb and plug it in… Well Windblows won't recognize the drive and claims it needs to be formatted. Nah that can't be. So I plugged it up to my personal Linux laptop to see what was going on. Sure enough I get the error:


Error mounting /dev/sda2 at /media/rj/TI105835W0O: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda2" "/media/rj/TI105835W0O"' exited with non-zero exit status 14: Windows is hibernated, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.




Okay – so I tried the delete hiberfile mount commands (sda2 and sda along with sdb2 and sdb...since it looks like fdisk is calling the external drive sdb1 and sdb2


sudo mount -t ntfs-3g -o remove_hiberfile /dev/sda2 /media/rj/TI105835W0O
and
sudo mount -t ntfs-3g -o remove_hiberfile /dev/sda /media/rj/TI105835W0O
And even
sudo mount -t ntfs-3g -o remove_hiberfile /dev/sdb2 /media/rj/TI105835W0O
and
sudo mount -t ntfs-3g -o remove_hiberfile /dev/sdb /media/rj/TI105835W0O


Doesn't matter what I type I get the same error:
NTFS signature is missing.
Failed to mount '/dev/sdb1': Invalid argument
The device '/dev/sdb1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


So – then I tried ntfsfix… again sdb1, sdb2 and sdb...
sudo ntfsfix /dev/sdb


But got the same error…
Mounting volume... NTFS signature is missing.
FAILED
Attempting to correct errors... NTFS signature is missing.
FAILED
Failed to startup volume: Invalid argument
NTFS signature is missing.
Trying the alternate boot sector
Unrecoverable error
Volume is corrupt. You should run chkdsk.




ALSO…


Meanwhile I also dropped the disk back into the old laptop and fired up windows just fine. It works no problems. I read somewhere to try and “restart” the windows to get it shut all the way down… nope
I read to do a shutdown /s from the cmd prompt (as an administrator). It shutdown but still the same problems.


I also dropped in my Win 7 install disk and did a repair… It couldn't find anything wrong either.


What am I missing? I love Linux because you can normally BEAT UP any windows problem but this one has got me stumped.


Thanks again!

---

### Post by frank105 on 2015-09-18
Oh and - I guess I am afraid to try any of the other suggested repair steps as they look like they are intense and for damaged drive.  Mine boots fine.  I am guessing there is a "switch" somewhere or something that I have to add to a command or?  Simple for you - but stumping the heck out of me...

Thanks,

---

### Post by oldfred on 2015-09-18
Usually the issue is you left Windows hibernated or partition needs chkdsk.
And if Windows 8 or later it always is hibernated as fast start up is really hibernation.
And normal full shutdown is Windows is with fast start up on, so not really shutdown.
And you just about have to boot into Windows to correctly shut it down.

If NTFS signature is really missing then Windows would see it as RAW.

       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

---

### Post by frank105 on 2015-09-19
Hi Oldfred,

Thanks for the ideas. 

I feel like I have tried all of that though.  The drive is from Windows 7 and win chkdsk finds nothing.  I shutdown via the command prompt with c:\shutdown /s which I read was the down and dirty way to make sure it doesn't hibernate.  I searched via windows for an old hibernate file (hibersys?  right?) and couldn't find any.  

Any other thoughts?

Thanks,

---

### Post by Mark Phelps on 2015-09-19
Win7 doesn't use the Win8 FastStartup form of hibernation, so when you shut it down, it does not go into hibernation. 

The old hibernation file is hiberfil.sys -- see the linked Win7 forums post for more details: [http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html](http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html)

---

### Post by frank105 on 2015-09-22
Thanks for the confirmation - hibernation is disabled.  I have looked and there is no hidden or visible file named hiberfil.sys

But it still gives me the same errors.  What else can I try?

---

### Post by oldfred on 2015-09-22
If you just are copying data, remount as read only with the ro parameter as mentioned in error message.

       Manual mount read only may work to copy data
sudo mount -o ro /dev/sda2 /mnt

Or you may have to include the ntfs parameters rather than default?

---

