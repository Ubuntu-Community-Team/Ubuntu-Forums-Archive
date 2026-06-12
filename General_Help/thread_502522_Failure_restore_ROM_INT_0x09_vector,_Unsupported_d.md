---
title: "Failure restore ROM INT 0x09 vector, Unsupported dos, device driver or TSR."
date: 2007-07-16
forum: General Help
---

### Post by shirinovitch on 2007-07-16
Hi,

I tried to install Wubi on an old computer to be used by the kids while windows crashes all the time.

The installation went well until I pushed the 'reboot'-button.
I got no bootquestion asking me what to choose : ubunto or windows.

Therefore I tried to run it myself and executing the wubildr.exe file
Here I get the above message in a DOS-window :
Failure restore ROM INT 0x09 vector, Unsupported dos, device driver or TSR.

I don't get any further, what to do next/now please ?

System info :
Windows millenium
128 MB ram
20 GB hd

---

### Post by ago on 2007-07-16
I am not sure windows millenium is supported. From the little I have read it uses a different booting mechanism from w98/nt/xp/vista, and I have no winme to test with. You might want to use the LiveCD

---

### Post by shirinovitch on 2007-07-16
Thanks for the quick response.
I especially used wubi because I can't use the livecd.
The cd-rom drive is broken.

---

### Post by ago on 2007-07-16
Bean123 and tinybit might be able to help you, I do not know much about winme boot process.

---

### Post by tinybit on 2007-07-17
winme support on grub4dos is not tested yet.

but you may remove config.sys and autoexec.bat and run  wubildr.exe again.

You can also try to enter safe mode of winme(if possible), and double click wubildr.exe from Windows explorer.

If both failed, you may try to run wubildr.exe from a floppy DOS:

Create a bootable floppy using your winme, and you can boot to DOS with this floppy.

At the DOS prompt, type wubildr.exe and press enter.

This will boot to the grub console, or your wubi installer should be started.

---

### Post by shirinovitch on 2007-07-17
OK, but NEW PROBLEM

I figured out that I had to run from a real MS-DOS instead of MS-DOS in Windows.
In Windows Millenium, there's no possibility at startup to choose MS-DOS, so I had to find something else (because I don't have floppy's anymore to make a bootable disk).

Perhaps for other users, I found a solution at :
[http://www.geocities.com/mfd4life_2000/](http://www.geocities.com/mfd4life_2000/)

Now, I have a bootloader to choose Ubuntu.
It starts and after a few seconds it hangs after the following message :
no RAID disk.

What to do now ?

Thanks in Advance,

---

### Post by ago on 2007-07-17
If you have a prompt look at logs under /tmp
Always start with a fresh install

---

### Post by tinybit on 2007-07-18
Just for the original old problem: Try dual booting MS-DOS/FreeDOS and WinME, Then you would be able to run grub4dos from MS-DOS/FreeDOS.

Or Try to place a line of device=wubildr.exe as the first line of config.sys for WinME and see if it could work.

---

