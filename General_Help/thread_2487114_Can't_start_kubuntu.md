---
title: "Can't start kubuntu"
date: 2023-05-23
forum: General Help
---

### Post by bjngchn on 2023-05-23
This installation sucks completely.

Today, I tried to shutdown the computer.
What happened:
I was left with a moving but nonfunctional cursor.
Shutdown didn't happen even  after minutes.
Computer didn't become functional either.
Just a nonworking screen  with a movable cursor.
How worse could things be, except laptop's exploding on my face.
There were no programs started  by me, and still running.
I had  disabled almost  all desktop effect, wireless, blutooth,..Still when I do ps ux. I see 50 entries: WHAT are they FOR.

Anyway, computer failed for no reason at all.
Not a very old one. I would buy dozens of the same if I can find, because new ones are more and more eviI..

Let me also mention that  Discover is mentioning updates,
 but hash is wrong (WHY, what the hell, how can this even be possible, it was initially correct, who screewed it up, I mean
who else except ubuntu itself could possibly do it. even a  *ware can't do such things I suspect)


WHATEVER,  NOW I HAD TO SHUT THE COMPUTER DOWN BY FORCE.
Hours later I came back, tried to run the computer, instead of asking me passwds, 
computer show me a command line saying:

grub>_


and above that command line it says Minimal BASH+like line diting is supported. TAB lists possible command completions. Anywhere else TAB lists possible device or file completions. GNU GRUB version 2.04


NOW I NEED A TRICK TO START THE COMPUTER.



Previously it would start normally, I would type encryption and then user pw.


Now I'm not shown any options.

It was not my choice to enter grub. It is forced without reasonable excuses or alternatives.
As if we all need to be linux experts.

Will F2, F8, F10 work? Bios etc?

---

### Post by oldfred on 2023-05-23
> I had  disabled almost  all desktop effect, wireless, blutooth,..
And you expect it to work the same? Some of those may be required.

I do turn off bluetooth as my system does not have it. But do not turn off Wi-Fi as Internet is required for updates.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If install is otherwise ok, you can often type in a bunch of commands to manually boot?
If you want those, I can post that.

---

### Post by bjngchn on 2023-05-23
Computer must be ok. Was able to do memory test, and quick harddrive test, those passed.
Everything was working until a  few hours ago. 

Just need to 

avoid grub>_  prompt, 
and start the laptop  normally.

---

### Post by bjngchn on 2023-05-23
For example , found this web page, but can't locate root. Even if I did, not sure about the rest.   [https://www.linuxfoundation.org/blog/blog/classic-sysadmin-how-to-rescue-a-non-booting-grub-2-on-linux](https://www.linuxfoundation.org/blog/blog/classic-sysadmin-how-to-rescue-a-non-booting-grub-2-on-linux)  Wondering whose idea is it to show me a grub prompt, because it was never requested.   I'm doing the same thing and expecting the same result, so I must be smart? Or are computers are stupid, because they act differently under same conditions, or some stuff are running outside our control.

---

### Post by oldfred on 2023-05-23
You get grub> because you have a version of grub looking for something that does not exist.
Most common is that you installed twice, once in BIOS/Legacy/CSM mode and once in UEFI. Then changed default boot settings in UEFI and it is trying to boot incorrect copy of grub.
Or you corrupted partition by forcing shutdown and grub cannot find your install. You then need to run fsck or e2fsck on your ext4 partition(s) from your Ubuntu live installer booted in live mode.
If encrypted, you still have to decrypt partition.
If you have encryption, standard rule is you must have good backups. File corruption inside the encryption or the encryption keys will prevent repair.
You then just reinstall & restore from your backup. (rule applies whether Linux or Windows).

Post link from Boot-Repair if you still want help.

---

### Post by bjngchn on 2023-05-24
Ok. Every word and sentence  is extremely technical for me. Now, I have grub> prompt. So this prommpt must have a function. Otherwise why is it there.  Do I need an external device or internet connection to fix this? What if I do a hardware test, the long one lasting 2+ hours, and the test is passed, then can this make things simpler, because it would mean some possibilities are eliminated? Let me try this test.  Ok, just started, it will last 2:45 hours.  The title says. HARDWARE DIAGNOSTICS UEFI   ............................................EDIT: Hardware test passed (long version)

---

### Post by oldfred on 2023-05-24
See post #2.
Report will tell us a lot about your system, so we can suggest what will be correct way to fix it.
Do not run its suggested auto-fix. Usually ok, but sometimes makes it worse, so we need to review report.

---

### Post by bjngchn on 2023-05-24
Looking for an easy solution. 
Somene posted this video:
  [https://www.youtube.com/watch?v=LFj_yqk6AUI](https://www.youtube.com/watch?v=LFj_yqk6AUI)   
Everyone is happy about it. This a rare thing. 
And here are the list of commands (a commenter typed it for me, just copying)  

set prefix=(hd0,gtp2)/boot/grub  
set root=(hd0,gtp2)  
insmod normal  
normal 

 No errors. But after NORMAL command above, nothing happens/  What can be the reason.   (other solutions: I may not even be able to understand, do correctly, or have confidence in)

One problem, I can't locate /root folder or any other folders like /swap, /home ..others see. I just see thing like lost+found/ ..vmlinuz generic,..

---

### Post by oldfred on 2023-05-24
You have to type gpt correctly.
But actually you do not need either msdos nor gpt, but can use (hdX,Y) where hdX is drive and  Y is partition.

Most users that have issues find Boot-Repair a lot easier to use & then it can fix issues. Everything else is a shot in the dark.

If you want to manually boot and second partition is / (root) and you do not have /boot partition, nor LVM install.

ls # Do you see (hd0), (hd0,2) ? If so, run the next command. Change if not hd0,2.
```
configfile (hd0,2)/boot/grub/grub.cfg

```
OR:
```
set prefix=(hd0,2)/boot/grub
set root=(hd0,2)
linux (hd0,2)/boot/vmlinuz root=/dev/sda2 ro
initrd (hd0,2)/boot/initrd.img
boot
```

But that does not fix error, just allows you to get into system.
Boot-Repair can fix it.

---

### Post by bjngchn on 2023-05-25
Thanks to all. Not solved yet. Even a temporary solution can be ok, because I would put computer
into sleep and never shut it down (and I can do it, under my control, unlike what computers with unremovable batteries doing).

Found this one:

[https://www.youtube.com/watch?v=ENn9f2ipjwo](https://www.youtube.com/watch?v=ENn9f2ipjwo)


I typed their commands , and replaced msdos with gpt2.

linux (hd0,msdos1)/vmlinuz root=dev/sda1 
 initrd (hd0,msdos1)/initrd.img   
boot
(this part copied from description of the video)

Output was almost the same (and my output was longer).

after boot  command, I'm asked encryption key.
So I must be very close.

I'm  at (initramfs)   (instead of grub>)right now, whatever it means.
................
more detail: what happened between typing encryption key and, 
getting 

(initramfs)
line at the end:


...
*
cryptsetup: sda3_crypt" set up successfully
done.
Begin: Running.scripts/local-premount ... done
Begin: Will now check root file system ...fsck from  util_linux 2.34
Checking all file systems.
done.
done
Begin: Running /scripts/local-bottom ... done
Begin : Running /scripts/init-bottom ... mount: mounting /dev on /root/dev failed: No such file or directoy.
mount: mounting /dev on /root/dev failed : No such file or directoy
done.
mount: mounting /run on /root/run failed: No such file or directoy 
run-init: can't execute '/sbin/init' "No such file or directory
run-init: can't execute '/etc/init': No such file or directory
run-init: can't execute /bin/init': No such file or directory
run-init: can't execute '/bin/sh' : No such file or directoy
run-init" can't execute ' ': No such file or directoy
No init found. Try passing init=bootarg.

BusyBox v1/30.1 (Ubuntu 1:1.30.1-4ubuntu6.4) built-in shell (ash)

Enter 'help' for a list of built-in commands

(initramfs)

;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
QUESTION: what now. maybe I'm close at this point.

Maybe I must also mention the part before acceptance of encryption...
talks about, topology, table, graphics,..
One eror I see there is:

Volume group "vgkubuntu" not found
Cannot process volume group vgkubuntu
Please unlock disk sda3_crypt:

and the rest is typed above *

---

### Post by bjngchn on 2023-05-25
.so I'm at    (initramfs)  prompt.  What does it mean. No idea, but I passed encyrption level, and when I do ls, I see folders like root, kernel, initm lib, run, sbin, var, usr, proc, tmp, cryptroot, dev, lib, shbin, scripts, etc but not home directoy.  So output for ls is vey different from grub>_ prompt.

---

### Post by oldfred on 2023-05-25
Do not understand why you do not want to use the easy solution: Boot-Repair per post #2.

This user's install was in a NVMe drive, change to  your partition.
From initramfs
cryptsetup luksOpen /dev/nvme0n1p3 nvme0n1p3_crypt and entering the password, then: exit It will boot.
Boot-Repair Mount encrypted partition, update-initramfs missing partition on boot error,  /etc/crypttab setting
[https://unix.stackexchange.com/questions/677381/lost-boot-option-debian-after-switching-between-uefi-and-legacy](https://unix.stackexchange.com/questions/677381/lost-boot-option-debian-after-switching-between-uefi-and-legacy)

---

### Post by bjngchn on 2023-05-25
Is this a command?

> **oldfred said:**
> 
cryptsetup luksOpen /dev/nvme0n1p3 nvme0n1p3_crypt 

Boot repair disk downloaded. And burning it is another problem.
I can insert almost empty flash disk into this working laptop, but it also has
something else (burnt kubuntu). 

How will I burn it, looks like I need to install something else to burn it.
What a mess, why is not everything in one place.
I need to trust each separately.

If I insert (mount ? )flash-disk with burnt boot-repair file into non-working laptop,
what will happen, I mean it can try to run boot-repair, but it can also 
try to install kubuntu from the other file.

And can I be sure my encryption or root pw's,
 or home folder data won't be transferred anywhere, and no backdoors would be created.


Wondering whether flash-disk is what everyone calls live-USB.

---

### Post by oldfred on 2023-05-25
USB live installer or flash drive or pen drive or various other names.

If you have your Ubuntu live installer/flash drive can you not boot system it on system that is not working?
And then add Boot-Repair as the instructions say under option 2 use ppa to add to your install?

I trust Linux applications a whole lot more than Windows & Windows applications.
But even with Linux, my email gets a lot of phishing, click here type emails. I do not know how many free things I have missed out on. 
And verify of password on bank accounts for banks that I have never used.

---

### Post by bjngchn on 2023-05-25
I click on boot-repair ISO file, and it says insert CD or DVD,  but boot-repair instructions says , use flash-disk.    
So, what now. Do I need to install something else first ?
Once flash is ready, do I need to change boot order, and if so
will I need to bring it back, or will it happen automatically?



     (All these sound like tricks to force us to use risky software. Linux is of course much more reliable than windows which is closed source. But there can be backdoors/tricks in linux together with their excuses, also..for example firefox was notworking on some sites because of being old (cloudflare's excuse), after 2 types of upgrades, it is still old, plus bookmarks gone.)

---

### Post by oldfred on 2023-05-25
If you downloaded the Boot-Repair ISO, which I do not suggest, you have to create it by installing with install software onto a flash drive to make a live installer.
If you use the Ubuntu live installer, you can just boot it and install Boot-Repair into your live installer. Live installer cannot be updated as it is like a DVD/CD but on flash drive. So if you reboot, you have to install the ppa again.

---

### Post by bjngchn on 2023-05-25
Looks like I'm forced to  connect to internet when doing all these. I prefer not to. 
I must create (somewhere on a working computer ), and then insert+run the tool (in failing computer), and let do its job. 
Why connect to internet if it is not for creating backdoor, stealing pws and files etc.
I'm still far away from understanding how to do this;. Here is one site talking about it:
[https://askubuntu.com/questions/226061/how-to-install-the-boot-repair-tool-in-an-ubuntu-live-disc](https://askubuntu.com/questions/226061/how-to-install-the-boot-repair-tool-in-an-ubuntu-live-disc)

---

### Post by bjngchn on 2023-05-25
Looks like I'm forced to  connect to internet when doing all these. I prefer not to. 
I must create this tool (on a working computer), and insert+run the tool (on a nonworking computer), 
and let do its job. 
Why connect to internet if it is not about  creating backdoor, stealing pws and files etc.
I'm still far away from understanding how to do this;. Here is one site talking about it:
[https://askubuntu.com/questions/226061/how-to-install-the-boot-repair-tool-in-an-ubuntu-live-disc](https://askubuntu.com/questions/226061/how-to-install-the-boot-repair-tool-in-an-ubuntu-live-disc)
and maybe this one is simpler version of the same thing:
[https://fedingo.com/how-to-repair-ubuntu-18-04-from-usb/](https://fedingo.com/how-to-repair-ubuntu-18-04-from-usb/)

Wondering how encryption will affect all these. 
Connect to internet while typing encryption key or root pw: would be horrifiying.

---

### Post by yancek on 2023-05-26
> Looks like I'm forced to  connect to internet when doing all these. I prefer not to.  

The reason you have to connect to the internet is because the boot repair software is in a physical location on a server in some other location, other than your home.  Did you read the suggestions by oldfred above or the instructions on the boot repair site?  At the boot repair site at the link below, you scroll down to where it shows 2nd option and follow the simple instructions.  You just installed Ubuntu so you have a USB you can boot which you used to install Ubuntu.  Boot that again and you can download and run the Create BootInfo Summary option of boot repair.  There should be no reason you can't boot the USB from the non-working machine if you just used it to try to install Ubuntu.  Use the same procedure again.  When boot repair finishes, it will give you a link you can post here for members to help. 

Using the live USB which you used to install Ubuntu is safe as it is read only and any changes made on it will be lost on reboot.  Read through oldfred's posts as he explains all this.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by oldfred on 2023-05-26
If system is ever going to be used on Internet, you must regularly connect and do updates. Not updating is more dangerous than just about anything for both Windows & Linux.And even your Raspberry Pi.

---

### Post by bjngchn on 2023-05-29
If I have to connect internet, I see bad intentions here. Why don't they make their program  downloadable, and locally usable. this means they want our critical data.

So is there a way that I can copy  data (in unencryypted form)., possibly without full normal  access. Then I would format the computer because it is problematic: correct hash code became incorrect for no reason, informing about updates, but update is not possible. whose fault is this. Anyway, time to start over, but I must  make a copy of home directory contents in unencrypted form first.

---

### Post by VMC on 2023-05-29
> **bjngchn said:**
> This installation sucks completely.

Today, I tried to shutdown the computer.
What happened:
I was left with a moving but nonfunctional cursor.
...
I had the exact same issue regarding cursor with no Panel, if this is what your referring to.
This happened several times. The cursor only, and no panel. Had nothing to do with Grub.
@bingchn, if this is your issue also, go [here]("https://bugs.launchpad.net/ubuntu/+bug/2021502") and add any significant info. I couldn't find help from log files.
Finally installed another KDE distro, and haven't had issue once.

---

### Post by oldfred on 2023-05-29
@VMC
Have had some similar issues. Added to bug, but not something I think will be easy to isolate. 
Several times screen has just lost all Icons & panels. Mouse works. Not consistent enough I can even identify if another program or some setting somewhere.

---

### Post by bjngchn on 2023-05-30
So, I want to get rid of  grub>_ prompt  on that laptop which has encrypted kubuntu  
and some files which would take a lot of time to recreate, 
so I want to format the laptop with newest LTS encrypted kubuntu, and 
before this I want to save all or important /home files (may want firefox bookmarks as well).  

Questions:

1.CAN I DO IT?  (without boot-repair): using a flash disk with burnt kubuntu .ISO file. 
2..Also wondering what burning means, how is it different from copying.  
3.Of course at some stage I will have to type encryption key. 
Once I start using the computer, can I move out the flash disk?


4. If yes(number 1):  How, I mean, do I need to modify BIOS/UEFI/BOOT preferences etc?
Do I need to decide on these parameters, based on current system, or the flash disk's .iso file?

Important question here is of course the number 1. above.  Can it be done,
there is  grub prompt problem, but still I want to be able to login(encryption+user)
via flash disk (used to install the kubuntu initially, or something similar).

---

### Post by oldfred on 2023-05-30
You often can manual boot:
At grub> you have some limited commands.
Do you have a separate /boot partition? Some now add a grub module that lets you boot directly into encrypted lvm & ask for the passphrase.
[https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)
"The default is normally set by GRUB at startup based on the value of &#8216;prefix&#8217;" and "'prefix' is normally set by GRUB at startup based on information provided by grub-install"

Sometimes you can just boot with this example uses ls to find that /boot is in partition 5 of first drive:
ls # Do you see (hd0), (hd0,5) ? If so, run the next command. Change if not hd0,5.
configfile (hd0,5)/boot/grub/grub.cfg
Not sure with encryption whether it works or not.

If you have encryption there is another module you need to load, but I do not know encryption. This example has / in sda1 or hd0,1. My system boot drive is always hd0, and often flash drive is hd0 when used to boot, so install is really hd1 or hd2.
grub> ls
grub> ls (hd0,1)/
grub> set root=(hd0,1)
grub> linux /boot/vmlinuz root=/dev/sda1
grub> initrd /boot/initrd.img
grub> boot

Some of the users here say if it takes more than an hour to fix, better to just totally reinstall & restore from backups. They also are the ones that say with encryption you must have really good backup procedure as corruption in the encryption can prevent boot or decrypting it. 

Burning may be still used but that was with a laser to a CD/DVD. Become more of a generic term for creating a bootable live installer.

Every system I have seen except HP and maybe one other supports use of efibootmgr and its -o  parameter to change boot order.
man efibootmgr

You also can chroot into your install & run repairs from inside it. CH or change ROOT.
UEFI chroot, must include ESP - efi system partition
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
 chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)

---

### Post by VMC on 2023-05-30
When you get grub prompt, type set, and it will show you what partition grub is using.
```
lsblk -f
``` will give us your HD info.[not sure if you already supplied that info or not]

---

