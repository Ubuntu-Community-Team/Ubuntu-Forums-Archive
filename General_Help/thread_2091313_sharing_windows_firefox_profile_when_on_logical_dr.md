---
title: "sharing windows firefox profile when on logical drive"
date: 2012-12-04
forum: General Help
---

### Post by georgec32 on 2012-12-04
Hi all,

About a year ago I had my laptop set up as a dual boot, Ubuntu 10.10 and Window$ 7.  I wanted to share bookmarks & other setup 'stuff' for firefox and also for thunderbird between windows and ubuntu.  I had made a FAT32 logical drive, called it WINLIN WindowsLinux), and put all my thunderbird & firefox profiles in there, then used profile manager to point to that profile.  I had trouble at first because I had to auto-mount the drive when booting into ubuntu, but got it all working just great.  Used it for about a year.

A while back, my hard drive crashed & I re-installed Win7 but did not put unbuntu on.  Then last week I got a new HD for my laptop & decided to put ubuntu back on.  

My problem:  I'm auto-mounting the WINLIN drive, it shows up on my ubuntu desktop, I set the profile to the proper one, but I'm getting the 'firefox is already running' message when I try to open it up.  I can look thru the files on WINLIN to make sure it's mounted, but still get the same error.  I've tried blowing away the profile & creating it again, but same result.  I'm also having the exact same issue w/ thunderbird, so it isn't anything about firefox ... it's something with the way I'm mounting the WINLIN drive, or something like that.  I've checked with two apps to make sure I can read/write/execute from WINLIN (used StorageDeviceManager and MountManager) .. I can't see anything wrong at all.  

Any suggestions?

Thanks in advance .. and if any of you are in Maui next week, I owe you a beer for any solutions, answers, wild guesses, pretty much anything :)

cheers,
george

---

### Post by georgec32 on 2012-12-04
BTW, just a quick follow-up.  I tried to google this but couldn't find anything.  The time I got this working, someone on this forum told me to edit FSTAB to add the following line after the auto-mount line:

after I had added:
UUID=9618-FF84 /media/WINLIN vfat defaults 0 0 

he told me to delete 'defaults 0 0' from the previous line and add:
defaults,uid=george,gid=george,dmask=0027,fmask=0137 0 0

That worked great when I had this working.  I had to look up the new entry on my current installation for UUID but everything else should be the same.  I added that stuff to FSTAB & now on booting it tells me it has trouble mounting and to press 'S' to skip mounting etc .. no idea what's going on there.

george

---

### Post by georgec32 on 2012-12-04
problem solved :)  I edited FSTAB and made the auto-mount line:

/dev/sda6 /media/WINLIN vfat defaults,uid=george,gid=george,dmask=027,fmask=137 0 0

Both Firefox and Thunderbird are working great now.


george

---

### Post by oldfred on 2012-12-05
I stopped using FAT32 except on smaller devices where the camera or other requires it. FAT32 has a max file size of 4GB and does not have a journal so chkdsk takes longer and has less chance of recovering from abnormal shutdowns.

This is my NTFS setting for my shared. I have my Firefox & Thunderbird profiles in my shared. These settings are for NTFS only. 

```
# Entry for /dev/sdc2 :
UUID=44332FD360AA9657 /mnt/shared ntfs-3g defaults,uid=1000,nls=utf8,windows_names 0 0
```

       Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

            [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

### Post by georgec32 on 2012-12-05
Thanks Fred.  I set this up as FAT32 some time ago because I thought ubuntu had trouble reading NTFS and have just kept it since that time.  Perhaps the next time I feel frisky, I'll set up a partition in window$ as NTFS and copy my profile files to that one & see if I can follow your lead .. then I can blow away the FAT32 drive etc.  Thanks again for the help & advice!

george

---

