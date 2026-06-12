---
title: "cannot boot windows xp"
date: 2008-05-13
forum: General Help
---

### Post by ustpandi on 2008-05-13
i have two hard disks, one with windows xp installed and one with ubuntu 8.04. since i installed ubuntu windows cannot boot.
it says "ntldr missing". i tried with various guides on internet but none seems to work

---

### Post by lemming465 on 2008-05-20
Post the output from *sudo fdisk -l* and we can offer more specific advice.  In general, you probably have to boot an XP install CD [in recovery mode]("http://support.microsoft.com/kb/314058"), and then run the *fixboot* utility.  That probably won't trash the MBR where Grub is booting Ubuntu; if it does you'd then have to follow the windows repair step with booting an Ubuntu CD and doing a grub-install.  I think the latest live CD's have a boot option to help out with that.

---

### Post by ibuclaw on 2008-05-20
Wow, this post is 1 Week Old...

Erm, ntldr is essentially the MS startup kernel.

It is located in **C:\ntldr**, but during a Windows boot you never really see this as it is usually hidden with the "**ATTRIB +H +S +R**" DOS command.

I would recommend that you mount the Windows Partition and check that the file is there. 

If it isn't, you must download a replacement one and put it in that location in it's place.

But before you try and Boot Windows, while under Linux, check that the ntldr file you downloaded is legitimate first:

Opening up the terminal and cd to the extracted ntldr location.

Then type in:
[PHP]md5sum ntldr[/PHP]
And you should get the reply
[PHP]9ec920f4179d45af3a6638a083d39c85  ntldr[/PHP]

Else, your boot.ini file is pointing to the wrong harddrive, and the number needs upping by one.

Regards
Iain

---

### Post by jimv on 2008-05-20
Also, you should have NTDETECT.COM, BOOT.INI, and NTLDR all on your C: drive for XP.  If NTDETECT.COM and NTLDR aren't there, you can grab them off of your XP CD in the i386 folder.  Boot.ini has to be made from scratch.

Here's the contents of a default boot.ini file for XP:

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=&#8221;Microsoft Windows XP Professional&#8221; /fastdetect
```

Just replace 'partition(1)' with the number of whatever partition XP is on.

---

### Post by Herman on 2008-05-20
I agree with what the above posters are already saying.

A look at your fdisk output would reveal whether you have Windows in a primary partition but with a partition number other than 1, or if you have Windows in a logical partition, in which case ntldr might really be missing.
Your fdisk output would also show if the hard disk you have Windows in is your first or second hard disk.

Usually people start with Windows in the first partition in their number 1 hard disk.

If hard disk Windows is in is plugged in as number 2 hard disk,you can use a pair of 'map' commands in GRUB to fool Windows into thinking it is still in the first hard disk and thus you don't need to edit your boot.ini file. [Chainloading on a non-first hard disk]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").
Otherwise, you can get Windows to boot up by changing the hard disk number in the boot.ini file if that's what's the problem.
It doesn't matter which way you do it, but editing GRUB's /boot/grub/menu.lst is normally easier.

If you still need more help, please post the output from 'sudo fdisk -lu', and a copy of the bottom portion of your /boot/grub/menu.lst file here in this thread. :)

---

### Post by lemming465 on 2008-05-20
> Wow, this post is 1 Week Old...
After responding to a few new posts and seeing that by the time I finished writing 5 other people had also responded, I started using Advanced Search to look for old posts with 0 replies.  It seemed like a good idea.

---

