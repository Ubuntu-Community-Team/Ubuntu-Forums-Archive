---
title: "common Thunderbird profile for Windows and (k)ubuntu - Linux side is &quot;busy&quot;"
date: 2007-02-03
forum: General Help
---

### Post by gregconquest on 2007-02-03
I'm having a problem with using Thunderbird and a shared profile between Windows XP and kubuntu 6.10. I asked about this issue on the kubuntuforums [http://kubuntuforums.net/forums/index.php?topic=13426.0](http://kubuntuforums.net/forums/index.php?topic=13426.0) but I think the issue would be the same in ubuntu and other linux flavors as well, and there are no answers forthcoming on the kubuntuforums. I'll crosspost the answer when it eventually comes out.

I'm running kubuntu 6.10 and Windows XP on separate partitions. I have successfully moved my Thunderbird profile to a common FAT32 drive as per [http://www.ubuntuforums.org/showthread.php?t=203524](http://www.ubuntuforums.org/showthread.php?t=203524)

I can use Thunderbird fine from the Windows partition, but not from the Linux side.
I have mounted this drive under kubuntu by editing the /etc/fstab as per [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Within fstab, I mounted the drive as
```
/dev/sdb1 /media/SATA320FAT32 vfat defaults 0 0
```
then when that didn't work as
```
/dev/sdb1 /media/SATA320FAT32 vfat rw,suid,dev,exec,auto,user,async 0 0
```

However, when I launch Thunderbird profile manager (from /usr/share/applications), I get the following error messages:
```
Profile in use
Thunderbird cannot use the profile "glc" because it is in use.
To continue, close the running instance of Thunderbird or choose a different profile
```
and if I try to launch Thunderbird itself
```
Close Mozilla-Thunderbird
Mozilla-Thunderbird is already running, but is not responding.
To open a new window, you must first close the existing Mozilla-Thunderbird process,
 or restart your system
```

Is this because:
1) I don't have the right write permissions for the FAT32 volume? I can see it from within Konqueror. Yet, under neither of the above fstab mount options am I able to drag and drop files to the drive. I don't have write permission.
2) I have to use a different name for the profile than I am using in the profile manager under windows? This doesn't seem likely.

Thanks for any help.
Greg Conquest

---

### Post by drs305 on 2007-02-03
I am also fairly new to Linux and I've had the same problem from time to time. I have done a lot of searching but haven't found the definitive answer. It seems likely  to be a corruption of one of the prefs files or something within the Firefox or Thunderbird profiles and not Linux (at least in my case). It's caused by a premature termination of Firefox/Tbird, perhaps when two copies were still running. 

While I can't provide a solution, I can give you a rough workaround. I had to create a completely new profile and then used FEBE/CLEO to import settings. You can't copy ALL the files completely because it's one of them that is corrupted and casues the error message. Anyway, once I got a new version working, I immediately also created a backup profile, and this time you CAN just copy all the files over to a new profile (but not the same name as the original). If it should freeze again, delete the offending profile and use the files from the backup/uncorrupted one.

You may find that if you do this once you won't have the problem again. I've gone about a month without it occurring again.

Good luck and hopefully someone with more knowledge can help us both.

---

### Post by gregconquest on 2007-02-04
Thanks for this, drs305. But wouldn't my accessing and using and changing the Thunderbird profile from the Windows side repeatedly and successfully mean the profile is not corrupt? It is being recreated each use, right? Did you have the seemingly corrupted profile from the Linux side yet were able to use it from the Windows side also?

Also, my inability to drag and drop files on that shared fat32 drive seem to indicate that the problem is independent of the Thunderbird profile. I'm guessing that until I can move files around on that drive (in Konqueror in kubuntu) as it is mounted from the fstab line, I won't be able to isolate the Thunderbird profile issue.

Greg

---

### Post by gregconquest on 2007-02-04
I got it all working! The only problem was with the write permissions I had under the mount options as specified in fstab. Below is a copy of the answer as it came from
[http://www.ubuntuforums.org/showthread.php?p=2107144#post2107144]("http://www.ubuntuforums.org/showthread.php?p=2107144#post2107144")
**mounted 2nd internal drive, but write permissions wrong**
> 
Yeah! taurus. It worked :)  I did the following:
1) From Konsole (or other terminal)
```
kdesu kate  /etc/fstab
``` (for kde / kubuntu; for gnome / ubuntu -- gksudo gedit /etc/fstab) (correct me if I'm wrong:KS )

2) I altered the previous relevant fstab lines (mentioned at the beginning of this thread) to this:
```
# FAT32 drive for common Windows/Linux application data
/dev/sdb1 /media/SATA320FAT32 vfat iocharset=utf8,umask=000 0 0
```
The first line is a comment (# comment . . .)

3) Save/close/exit all settings, files
4) Reboot

I can now use Konqueror to create/move files on the drive in question. The page below spells this all out in more detail:

[http://lgacorp.wordpress.com/tag/ubuntu-linux/](http://lgacorp.wordpress.com/tag/ubuntu-linux/)
under the entry:
   Hard Disk Drive
   December 12th, 2005 · No Comments
   Ubuntu Linux commands
   Mounting HDD&#8217;s fixed or USB / NTFS or Fat32,
   editiing for automount on reboots.

I still don't know why "iocharset=utf8,umask=000 0 0" works, and may be the best choice, but is not generally mentioned in the most easily found Q&A's dealing with this issue. Check the keywords:
fstab mount options
and you won't find this answer. Till now, perhaps. I'll post this message text in the Windows/Linux Thunderbird common profile and data [http://www.ubuntuforums.org/showthread.php?t=352833]("http://www.ubuntuforums.org/showthread.php?t=352833")

:guitar: 
Greg Conquest

After I did the above, I started Thunderbird regularly (I had already chosen the profile location, it just couldn't be accessed). Thunderbird opened and just worked. One of my filters within Thunderbird was off. I had to re-associate the filter with its target folder, but other than that, it was OK.

Also, two other caveats:
- when drilling down to the thunder-profile, it is the last, unique folder that you select. Do not select a more top-level folder.
- and when launching the thunderbird profile selector from within linux, the other guides [http://www.ubuntuforums.org/showthread.php?t=203524]("http://www.ubuntuforums.org/showthread.php?t=203524")
[http://www.mozilla.org/support/thunderbird/profile]("http://www.mozilla.org/support/thunderbird/profile")
[http://www.linuxjournal.com/article/8761]("http://www.linuxjournal.com/article/8761")
only get as far as:
> On Linux, start Thunderbird with the the -profilemanager switch, e.g. ./thunderbird -ProfileManager (this assumes that you're in the Thunderbird directory).
I am assumed to be in the Thunderbird directory, but no one is saying where this is:confused:     I searched the net, but didn't come up with the answer. I right-mouse clicked on my Thunderbird icon, properties/configure, and there the directory was listed as
usr/share/applications
So then, I could find the home directory of thunderbird in konqeror (gnome's browser can do this too?:KS ), and then launch a command line from there (you could also do all this from terminal/konsole, I guess ):
1) kdesu konqueror (gksudo and then terminal ??? :KS  )
2) Find usr/share/applications (paste in search/navigation box at top)
3) Open mozilla-thunderbird-pm.desktop
Voila! The rest of the directions for altering the mozilla profile is written about more extensively than I can do in the other links above.

Next I'll try to share data between bittorrent clients. If I can keep my torrent downloads busy regardless of which OS I'm using, then I can "stay" in Linuxland. Only when I need to use DRM-infected mulitmedia or USB-connected multimedia devices with minimal linux support (Logitech webcams, . . .) will I need to switch over to Windows.

Greg Conquest ):P

---

