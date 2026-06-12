---
title: "Instability in CD/DVD drive detection"
date: 2007-09-05
forum: General Help
---

### Post by mthei on 2007-09-05
I've found issues similar to mine, but not quite the same.
Basically, I have a clean install of Feisty. When I upgraded from Edgy, I had the same thing in Feisty, although not in Edgy. Sometimes when I turn on my computer, all drives are detected correctly, and should I need to access files on a data DVD, all is well. However, sometimes when I log on, a second DVD drive is detected called CD-ROM 1, even though I only have one drive. When this appears, I cannot access certain DVDs, while I can at other times, however, there are some DVDs that do work even with the additional drive. It just so happens that the ones that do not work have been created with Roxio or K3b, while the ones created with GnomeBaker or even Nautilus will work. As mentioned, there are times when I am able to load the DVDs created with Roxio and K3b, while every other topic I've found on the subject of DVD mounting, none were able to work at all. When I get the issue where the drive won't read the disk, I usually just reboot until I no longer see the CD-ROM 1 in my computer folder, however, it's getting annoying, but I don't feel like switching distros just because of something like this. If anyone can give me any information as to keep it stable, that would be great. Countless searches over the past few months have been fruitless.

FSTAB is as follows, just for a second opinion:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=86999cef-9267-427b-b34c-297599fb7edb /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=86be7573-28d7-4f0e-b8b2-2392e2eab134 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

Edit: I should also add some of the error messages I get. When I click the CD-RW/DVD-+RW drive it says "Unable to Mount Media: There is probably no media in drive" and when I click on CD-ROM 1, it says "Unable to Mount Selected Volume: mount: special device /dev/hda does not exist".

Edit: Never mind, changing /dev/hda in the fstab to dev/dvd was able to stop the random duplicate entries. Currently all DVDs mounts, so let's see if it will work every time.

---

