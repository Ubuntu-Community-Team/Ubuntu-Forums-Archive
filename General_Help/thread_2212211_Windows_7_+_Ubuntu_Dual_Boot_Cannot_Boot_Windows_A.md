---
title: "Windows 7 + Ubuntu Dual Boot: Cannot Boot Windows Any More"
date: 2014-03-20
forum: General Help
---

### Post by vincent12 on 2014-03-20
Original Setup:
-Windows 7 on an SSD
-Extra storage on a hard drive

Dual Boot Setup:
-Windows 7 on an SSD
-Extra storage on a hard drive
-64-bit Ubuntu 13.10 on a third hard drive

I added a third drive and installed Ubuntu on it. Since then, I've been unable to boot Windows. (Ubuntu works fine.)

I tried two things:
1. sudo update-grub then restarting didn't help
2. As per this thread: [http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152) I tried to repair Windows with a Windows disc. However, once Windows boots from the disc, my USB keyboard & USB mouse stop working, so I can't do anything. (Unfortunately, I don't have any non-USB keyboards/mice to try.) All of my USB ports don't work at this point.

I found that the only way I can access Windows is by turning off my computer, removing the hard drive with Ubuntu, then booting from Windows works. (The repair actually succeeds.) Feeling hopeful about this, I turned off my computer, reconnected the hard drive with Ubuntu, and restarted the computer. Unfortunately, once I did this, Windows is no longer bootable again, and all of the problems are back again. (It's as if the presence of GRUB makes Windows not able to boot or something...?)

What can I do to fix this? Is there some way I can do a Windows boot repair from within Ubuntu? Any advice/help is much appreciated.

---

### Post by ajgreeny on 2014-03-20
It sounds as if you are using the wrong boot priority device to get to windows, though I do not fully understand how two windows installations work together with regard to bootmanagers.  I am also surprised that bootrepair has not figured this out for you.

I presume you have booted into Ubuntu and run ```
sudo update-grub
``` but if not, do so now and see if that works for you.

Try going into the BIOS/UEFI to change boot priority and set each hard disk as priority one by one.

---

### Post by vincent12 on 2014-03-20
sudo update-grub didn't help.

Changing the boot priority didn't work. Also, pressing F11 at start-up and manually selecting to boot from the hard drive with Windows did not work.

It may also be worth noting that when I installed Ubuntu, it told me that it didn't recognize any other operating systems on the computer (which I found odd).

---

### Post by ajgreeny on 2014-03-20
OK, I am now out of my depth and I can not help with any windows problems any more not having really used it since 2005.

---

### Post by dragonfly41 on 2014-03-20
For advice on triple boot configurations .. for your multiple drives .. search this forum .. **advanced search** .. 
looking for key words **triple boot** in thread titles only.

---

### Post by vincent12 on 2014-03-20
I'm not doing a triple boot... I'm doing a dual boot with a 3rd hard drive for extra space.

---

### Post by erind on 2014-03-20
From what you're describing, I *think* that might be a hardware conflict. I've had a similar problem not too long ago -- Windows (in one SATA drive) wouldn't boot if an IDE data drive was plugged in another SATA port, through an IDE->SATA adapter in **MASTER** mode. So I ended up removing that IDE drive completely off the motherboard, no issues since ... just something to keep in mind.

---

### Post by kc1di on 2014-03-20
Did you try boot repair?  it sounds like you may have installed grub in the ubuntu disk rather than in the MBR. 
you can download and run boot repair from here [https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")
Boot repair offers to save a error log for you online pay particular attention to the web address, if it does not fix the problem then you should be able to post the output of that file and it may have important info on what went wrong.

---

### Post by vincent12 on 2014-03-20
I ran the recommended repair for the boot repair, and it seemed hopeful. (Note that I ran it while in "Try Ubuntu" mode, running from the CD.) Here is the message it gave me once it was done:

```
Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/7128528/](http://paste.ubuntu.com/7128528/)

In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!

You may want to retry after deactivating the [Backup and rename Windows EFI files] option.

The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.
```

That didn't help, so I ran Ubuntu off the CD again and ran the BootInfo summary. This is what I got: [http://paste.ubuntu.com/7128583/ ]("http://paste.ubuntu.com/7128583/")

Any idea what I should do next?

---

### Post by kc1di on 2014-03-21
Ok turn the efi mode back on.  It was in legacy mode when you installed ubuntu and windows will not boot in Legacy mode. that's why grub can not boot it. 

after turning on EFI mode. run Boot-Repair again.  follow the on screen instructions it gives you very carefully.

---

### Post by vincent12 on 2014-03-24
Forgive my inexperience, but how do you turn EFI mode on?

From what I understand, when I run the BIOS-like process (to change things just like I'd do in BIOS), it says that I'm in the UEFI menu. Do I turn on EFI from there? Or do I need to use some command prompt?

---

### Post by oldfred on 2014-03-24
In your UEFI/BIOS you should have switches, but it varies by vendor and some low cost systems only have secure boot on/off. Then with secure boot off, it will auto switch to boot UEFI and if not found boot MBR. Or bot your choice. Others have secure boot on/off, UEFI on/off or legacy/BIOS/CSM on/off. But you cannot turn some options on in some cases, like there is no secure boot with BIOS on.

How you boot install media is how it installs. Or if you boot in UEFI mode it installs in UEFI mode.

Some examples of UEFI screens posted by others:

---

### Post by vincent12 on 2014-03-24
I feel much closer now.

I turned EFI on and reinstalled Ubuntu on my third drive. GRUB is successfully booting Ubuntu. However, it's still not able to boot Windows 7. It's listed as one of the options, but it fails when I try to select it.

Here is my Boot Repair log: [http://paste.ubuntu.com/7149452/](http://paste.ubuntu.com/7149452/)

---

### Post by vincent12 on 2014-03-24
When I ran Boot Repair to try and fix the Windows boot, it told me to retry with Secure Boot turned off. I listened to it, went into the UEFI, and turned off Secure Boot.

I ran Boot Repair again, and here is the new status: [http://paste.ubuntu.com/7149468/](http://paste.ubuntu.com/7149468/)

I'm restarting my computer now, and seeing if I can boot from Windows.

---

### Post by vincent12 on 2014-03-24
So close! I was able to boot Windows from GRUB, but once it's in Windows, my keyboard and mouse don't work. (They're both USB.)

With the exception of when I've messed around trying to dual boot Ubuntu and Windows, my USB keyboard & mouse have always worked for Windows.

Thoughts?

---

### Post by vincent12 on 2014-03-24
I figured it out. In the UEFI, I had USB detection turned to "UEFI Only". I changed it to "Auto", and now it's good.

Thanks to everyone that helped!

---

### Post by oldfred on 2014-03-25
Glad you got it working. 

And thanks for update on another UEFI/BIOS setting that may be needed. Seen others with keyboard issues.

---

