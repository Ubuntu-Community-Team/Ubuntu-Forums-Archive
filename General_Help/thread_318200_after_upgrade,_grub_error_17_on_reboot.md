---
title: "after upgrade, grub error 17 on reboot"
date: 2006-12-13
forum: General Help
---

### Post by aum11 on 2006-12-13
Installed the latest kernel updates and rebooted as requested....immediately got grub error 17.

Am writing this under the live disk at present....any suggestions please?

---

### Post by daller on 2006-12-13
There seems to be a general error with the upgrades today...

[http://ubuntuforums.org/showthread.php?t=318206](http://ubuntuforums.org/showthread.php?t=318206)

---

### Post by aum11 on 2006-12-13
Am not using nvidia so this seems to be a different problem.

Am on a dell 9300 laptop with ati radeon x300 graphics.

Updated a dell 1100 at the same time...no problems.

---

### Post by xabbott on 2006-12-13
Do you have more than one distro installed?

---

### Post by aum11 on 2006-12-13
It is a dual boot system, and windows still boots fine.

---

### Post by aum11 on 2006-12-13
Any suggestions please?

---

### Post by aum11 on 2006-12-13
Could someone please advise how to check that grub is correctly set up.

Am totally stuck.

Thanks

---

### Post by aum11 on 2006-12-14
really need some help with cleaning up this situation.  Cannot boot into Ubuntu.

Thanks.

---

### Post by confused57 on 2006-12-14
> **aum11 said:**
> really need some help with cleaning up this situation.  Cannot boot into Ubuntu.

Thanks.
The update may have changed your /boot/grub/menu.lst boot options?
You could try booting up with the live cd, open a terminal, enter:
```
sudo fdisk -l
```
You probably already know the -l is a small "L"

Determine the location of your root partition.

Then boot up your system, at the grub menu, highlight your entry to boot Ubuntu, press "e"
to edit...see if the root partition is correct, as well as the kernel /dev=?(from the info you got from the above command)...make changes if they appear to be wrong, then try to boot.

I don't really know, but worth a try...

---

### Post by aum11 on 2006-12-14
Thanks confused57 for Your help.  

I had already done that previously and had noticed that root was being referred to as hda3 instead of hda2.  I had changed that at boot time but still no success....but thanks to repeating it because of Your prompting I noticed that the second line was also incorrect...sda4 instead of sda3.

So changing that got me through but not before a scare.  It was time for the disk check after 30? boots...and it came up with a disk error???:-k   and rebooting was required, which went smoothly and here I am typing this to You under Ubuntu again.:D 

So I guess I need to make permanent changes to some file or other?  Do You know which file?

Also there are doubts about why it happened...I had changed nothing except applying the latest updates this morning.:-k 

And also the disk error.  How can I check that out as well?

Thanks so much for saving the confused.:-D

---

### Post by aum11 on 2006-12-14
I am guessing that I need to update /boot/grub/menu.lst?

---

### Post by Kegir on 2006-12-14
same problem after upgrading kernel.  I'm not sure what happened, I have grub on a floppy but I'm still getting error 17.  This is the second time in a couple of months an upgrade has maimed my system.

---

### Post by aum11 on 2006-12-14
Well now the problem is remedied with the above changes...that is, editing the incorrect partition addresses at boot time and then , once successfully rebooted, change /boot/grub/menu.lst to reflect those changes...

as to why it happened, I am totally in the dark...I have not gone anywhere near menu.ist or any other system file...I believe it must have something to do with the latest updates..

Previously I have advised others to take their time when applying fixes...just in case they introduce a problem...from now on I will follow my own advice!

Good luck and let us know if you have cannot restore the addresses.

Thanks to those who helped.

---

### Post by daller on 2006-12-14
Please go here, and help us clear up the situation...

[http://ubuntuforums.org/showthread.php?t=318206](http://ubuntuforums.org/showthread.php?t=318206)

---

### Post by confused57 on 2006-12-14
This may help explain what happened:
[http://users.bigpond.net.au/hermanzone/p15.htm#kopt](http://users.bigpond.net.au/hermanzone/p15.htm#kopt)

---

### Post by jdong on 2006-12-14
Hmm, are you guys saying that groot was modified by the update? That's be really odd...

---

### Post by emdeem on 2006-12-14
In my case, the latest update changed menu.lst such that "root=/dev/sda3" was changed to "root=/dev/sdb3".  Weird.  I do not have a second drive.

---

### Post by jdong on 2006-12-14
That's very odd. The kernel updates just call update-grub, which regenerates the list but doesn't mess with the #kopt line. It's very very peculiar that this would happen.

If someone has the time/patience to see if they can reliably reproduce this, it's definitely worth a bug report.

---

### Post by confused57 on 2006-12-14
> **jdong said:**
> Hmm, are you guys saying that groot was modified by the update? That's be really odd...
From reading some of Herman's posts & tutorials, it was my understanding that the kernel updates look at the #kopt=root...when updating the /boot/grub/menu.lst and I was wondering what aum11's kopt line displayed.  That would be interesting if the update-grub actually changed the root partition location in the kopt line, or if the drive may have been switched from another location since the original kernel was installed.

---

### Post by aum11 on 2006-12-14
In response to Your query confused57, here are the kopt lines from /boot/grub/menu.lst:

# kopt=root=UUID=96910b18-0b4d-414e-9e18-2f63735428f5 ro
# kopt_2_6=root=/dev/sda4 ro

It is incorrect.  Actually root is on sda3.

What comes to mind is that some months ago is that I removed a fat32 partition using gparted, and consequently  the root partition dropped from sda4 to sda3.  Home also dropped from sda7 to sda6.

It sounds as though somehow the latest update has returned to the old partition addresses.:-k 

Do I need to change these kopt entries?

---

### Post by mcduck on 2006-12-14
So then it's clear. Kernel updates don't change those default setting lines, but they are still the lines from before you removed that partition.. And now, when kernel updated it used that outdated information to regenerate your boot options..

Change those kopt lines to correct ones (you can get the UUID from /etc/fstab) and you shouldn't get the same problem with the next kernel update. :)

---

### Post by aum11 on 2006-12-14
When I went to /etc/fstab to get the correct UUID for root, which is sda3, I found that there is no sda3!

The following is probably it.  sda4 is actually the extended partition.

# /dev/sda4
UUID=96910b18-0b4d-414e-9e18-2f63735428f5 /               ext3    defaults,errors=remount-ro 0       1

So I suppose I change this entry from sda4 to sda3, as well as the kopt lines ?

---

### Post by mcduck on 2006-12-14
that sounds about right.

You can also check the correct UUID's with 'ls /dev/disk/by-uuid -alh'

---

### Post by aum11 on 2006-12-14
Thanks mcduck...is that scrooge by any chance?  All seems to be functioning perfectly.

If any others have this problem then You too may also need to change the kopt lines and /etc/fstab, as well as  /boot/grub/menu.lst.

All the best.:D

---

### Post by mcduck on 2006-12-14
no problem.

And the nickname hasn't actually got anything to do with Disney's comics, but that's a long story ;)

---

### Post by BrianH on 2006-12-15
After accepting the upgrades yesterday, I too am getting a grub error 17 on reboot.  My case seems slightly different though, my root partition is a software raid 5.  My grub setup looks correct it says root=/dev/md0.

What else could I look for?


I can get to a terminal session using the ubuntu install cd, and when I am in there I can actually mount /dev/md0 without any problems.  So the raid is not actually broken.

Why can't grub boot anymore?  Please help!  Everything was working so well before this update.  ](*,)

---

### Post by jdong on 2006-12-15
(1) If it's a kopt root=UUID..... line, you never need to change it unless you reformat the root partition, which is the only thing that'll change the UUID.

(2) What others seem to be reporting is either an erroneous kopt_2_6 line that was uncommented (mine shows it double-commented):
```

## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=7b6e9106-8810-4ec2-a101-0d595cedf28a ro

```

There is no kopt_2_6 line in the menu.lst that ships with Ubuntu.

Or, a previous change made to their system that wasn't applied until this kernel update.


In both cases that's not a bug introduced by the update, but it was introduced some time before by the user or a tool that the user used.

---

### Post by BrianH on 2006-12-15
> **BrianH said:**
> After accepting the upgrades yesterday, I too am getting a grub error 17 on reboot.  My case seems slightly different though, my root partition is a software raid 5.  My grub setup looks correct it says root=/dev/md0.

What else could I look for?


I can get to a terminal session using the ubuntu install cd, and when I am in there I can actually mount /dev/md0 without any problems.  So the raid is not actually broken.

Why can't grub boot anymore?  Please help!  Everything was working so well before this update.  ](*,)

Actually, maybe I need to ask a more basic question... is grub error 17 looking for my boot partition specified by the line:
root (hd0,0)
or is it complaining about my root partition which is in the kernel line as root=/dev/md0

I still have no idea what the problem is.

---

### Post by mdz on 2006-12-17
> **aum11 said:**
> In response to Your query confused57, here are the kopt lines from /boot/grub/menu.lst:

# kopt=root=UUID=96910b18-0b4d-414e-9e18-2f63735428f5 ro
# kopt_2_6=root=/dev/sda4 ro


The problem is that you have this kopt_2_6 line at all.  This isn't created by the installer, or placed there by any official tools.  You should remove it to avoid any further trouble.  The kopt line (the one with the UUID) is the only one you need, and this was managed automatically.

---

### Post by BrianH on 2006-12-18
> **BrianH said:**
> Actually, maybe I need to ask a more basic question... is grub error 17 looking for my boot partition specified by the line:
root (hd0,0)
or is it complaining about my root partition which is in the kernel line as root=/dev/md0

I still have no idea what the problem is.

My Problem has been solved.  It is similar to everyone else's problem.  My Grub root is actually is hd2,0 even though in Ubuntu it shows up as the first drive, sda.  I vaguely remember this when I first installed the system.  I could never figure out why that is. Anyway, the update reset it back to hd0,0 and that is why it didn't boot.

---

### Post by rusyear04 on 2006-12-19
me too help need :D

my problem seems to be similar, although not the same.
i did install a few updates (my laptop was last online on wednesday 13th) and was required to reboot the system.
at reboot GRUB gave me an error 17. it aparently changed the entry -i can/could fix that, but even if i give the right hdd-name (0,1) ubuntu does not start properly....

i begins boot-process and stops with an error...

any clue, anybody?
thanx!

---

### Post by rusyear04 on 2006-12-19
i'm doing a memtest now... the only (ubuntu) thing that works. because the recovery entry doesn't work either...

winXP (dual boot) is apparently starting...

---

### Post by rusyear04 on 2006-12-19
[COLOR="DarkRed"]:D fixed it :D

that li'll b..:-# did not just change the 'root' entry, but also the 'kernel' entry... had to change it too and now things are smooth again.
what a stupid mistake! ](*,) 

arrgh![/COLOR]

---

