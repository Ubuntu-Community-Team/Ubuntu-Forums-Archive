---
title: "Prevent external USB drives from sleeping"
date: 2023-10-17
forum: General Help
---

### Post by lazaruslong67 on 2023-10-17
I've been running 22.04.3 LTS for about a week now (as a new Linux user).  I've got 2 large USB hard drives connected to it for my Plex media server (running in a Docker container).

I'm noticing that if the drives haven't been used for some time, it takes awhile for a them to show files/folders in file manager - also Plex will take awhile to start streaming a video.

I checked BIOS and didn't see any settings specific to the USB ports causing this.  Also read an article where someone said to go into Disks, then Drive Settings and make changes there, but all my drives (including the internal nvme drive) have that option greyed out.

So looking for the best option to keep them "awake" (even if it means running some sort of periodic background job).

Thanks.

---

### Post by #&amp;thj^% on 2023-10-17
What type of Disk's 
```
cat /sys/class/block/sd*/device/{model,vendor} 
```

---

### Post by TheFu on 2023-10-17
Not all disks support preventing the spin-down power saving. Usually the larger, slower, cheaper disks don't.  This is especially true for USB connected disks.  USB really shouldn't be used for primary storage. Use SATA, eSATA, SCSI, or Infiniband instead.

Also, if you haven't already, make a plan to convert the media storage devices from NTFS to a native Linux file system.

You can also check into the **hdparm** tool so see if your disks will allow being told not the spin down.  The manpage for that command is extensive.  You'll definitely want to force mounts via the fstab file, not trust anything magically mounted under /media/.   

Lastly, Gnome Disks is pretty, but not always truthful.  Be cautious using it.

Some will say that I'm showing my biases.  That's true. I've just been doing this stuff for a long time and been burned many times. Please learn from my experiences, so you don't need to get burned to learn the lesson.

---

### Post by #&amp;thj^% on 2023-10-17
> **TheFu said:**
> Not all disks support preventing the spin-down power saving. Usually the larger, slower, cheaper disks don't.  This is especially true for USB connected disks.  USB really shouldn't be used for primary storage. Use SATA, eSATA, SCSI, or Infiniband instead.

Also, if you haven't already, make a plan to convert the media storage devices from NTFS to a native Linux file system.

You can also check into the **hdparm** tool so see if your disks will allow being told not the spin down.  The manpage for that command is extensive.  You'll definitely want to force mounts via the fstab file, not trust anything magically mounted under /media/.   

Lastly, Gnome Disks is pretty, but not always truthful.  Be cautious using it.

Some will say that I'm showing my biases.  That's true. I've just been doing this stuff for a long time and been burned many times. Please learn from my experiences, so you don't need to get burned to learn the lesson.
That sums it up nicely.

---

### Post by MAFoElffen on 2023-10-17
My choice would be hdparm. 

RE: [https://manpages.ubuntu.com/manpages/xenial/man8/hdparm.8.html](https://manpages.ubuntu.com/manpages/xenial/man8/hdparm.8.html)
If your disk does support APM, then
```

       -B     Get/set  Advanced  Power  Management feature, if the drive supports it. A low value
              means aggressive power management  and  a  high  value  means  better  performance.
              Possible  settings  range  from  values 1 through 127 (which permit spin-down), [COLOR=#ff0000]and
              values 128 through 254 (which do not permit  spin-down). [/COLOR]  The  highest  degree  of
              power  management  is attained with a setting of 1, and the highest I/O performance
              with a setting of 254.  A value of 255  tells  hdparm  to  disable  Advanced  Power
              Management  altogether  on the drive (not all drives support disabling it, but most
              do).

```
While thinking about what to set that to, these are my notes from the header of file /usr/lib/pm-utils/power.d/95hdparm-apm
```

# This script adjusts hard drive APM settings using hdparm. The hardware
# defaults (usually hdparm -B 127) cause excessive head load/unload cycles
# on many modern hard drives. We therefore set hdparm -B 254 while on AC
# power. On battery we set hdparm -B 128; this still does not guarantee
# disk parking, but is safer than causing lots of mechanical wear on disks
# as we seem to get currently with 127.
#
# Refactored from acpi-support's 90-hdparm.sh for pm-utils

```
And (man page hdparm)
```

       -S     Put  the  drive  into  idle  (low-power)  mode, and also set the standby (spindown)
              timeout for the drive.  This timeout value is used by the drive  to  determine  how
              long  to  wait (with no disk activity) before turning off the spindle motor to save
              power.  Under such circumstances, the drive may take  as  long  as  30  seconds  to
              respond  to  a  subsequent  disk  access, though most drives are much quicker.  The
              encoding of the timeout  value  is  somewhat  peculiar.   [COLOR=#ff0000]A  value  of  zero  means
              "timeouts  are  disabled":  the  device  will not automatically enter standby mode.[/COLOR]
              Values from 1 to 240 specify multiples of  5  seconds,  yielding  timeouts  from  5
              seconds  to  20  minutes.   Values from 241 to 251 specify from 1 to 11 units of 30
              minutes, yielding timeouts from 30 minutes to 5.5 hours.  A value of 252  signifies
              a  timeout  of  21  minutes.  A  value  of 253 sets a vendor-defined timeout period
              between 8 and 12 hours, and the value 254 is reserved.  255 is  interpreted  as  21
              minutes  plus  15  seconds.   Note  that  some older drives may have very different
              interpretations of these values.

```
To set as persistent, use /etc/hdparm.conf... That file is used by udev
RE: [https://manpages.ubuntu.com/manpages/trusty/man5/hdparm.conf.5.html](https://manpages.ubuntu.com/manpages/trusty/man5/hdparm.conf.5.html)

---

### Post by Dennis N on 2023-10-18
I once had an external eSATA drive which would spin down if not accessed in a 10 min period. I did not want it to spin down at all, so I made a cron job to run every 9 min using the touch command with a specific file on that drive. It worked.

---

### Post by lazaruslong67 on 2023-10-18
This seemed to do the trick for me:

```
sudo sdparm -l --save --set STANDBY=0 /dev/sd?
```

Just not sure if that will stick after a reboot yet?

---

### Post by lazaruslong67 on 2023-10-18
> **TheFu said:**
> Not all disks support preventing the spin-down power saving. Usually the larger, slower, cheaper disks don't.  This is especially true for USB connected disks.  USB really shouldn't be used for primary storage. Use SATA, eSATA, SCSI, or Infiniband instead.

Also, if you haven't already, make a plan to convert the media storage devices from NTFS to a native Linux file system.

You can also check into the **hdparm** tool so see if your disks will allow being told not the spin down.  The manpage for that command is extensive.  You'll definitely want to force mounts via the fstab file, not trust anything magically mounted under /media/.   

Lastly, Gnome Disks is pretty, but not always truthful.  Be cautious using it.

Some will say that I'm showing my biases.  That's true. I've just been doing this stuff for a long time and been burned many times. Please learn from my experiences, so you don't need to get burned to learn the lesson.

Yeah I learned about the "magic" mounts happening under /media/ - they didn't seem consistent so my drives wouldn't show up in my Docker container properly.  Got that fixed in fstab now.

Is there an easy way to switch to something like ext4 from NTFS?  I've got a 14 and 16TB drive, so kind of a PITA to move everything to another drive and back...

---

### Post by TheFu on 2023-10-18
> **lazaruslong67 said:**
> Is there an easy way to switch to something like ext4 from NTFS?  I've got a 14 and 16TB drive, so kind of a PITA to move everything to another drive and back...

Sure. Backup the data. Reformat the partition. Copy the data back.  Ensure you get the permissions correct AND don't be lazy with 777.  That's asking to have all the files deleted.
No matter what storage is used, backups are mandatory.  If you don't back up the data, it clearly isn't very important.  

For media, I only have 1 copy, not the normal 3-2-1 method. That's because media files are huge and seldom change. Either they exist or they don't.

BTW, any chance I could talk you out of plex?  Jellyfin is the similar alternative, but 100% F/LOSS and supports a wider range of media types without phoning home every click seen to the Plex guys.  For recording TV OTA, Jellyfin is much better.  The reason to use Plex or Jellyfin is for centralized media. If you only have 1 system to playback media on, then Kodi would be easier.  All of them use the same directory structure, so you can actually run all of them against the same TV shows and Movies and Photos and Music without impacting the others.

There are many things where plex is "slicker", but there are also real privacy failures in Plex. Looking at my network logs back when I ran Plex, only my Roku box tried to phone home more often.  Every damn click was sent.  If you aren't willing to change from Plex, please, please, please, follow the FBI recommendations and put it onto a completely different subnet away from desktops and other computers with important things.  [https://www.fbi.gov/contact-us/field-offices/portland/news/press-releases/fbi-tech-tuesday---building-a-digital-defense-against-the-internet-of-things-iot](https://www.fbi.gov/contact-us/field-offices/portland/news/press-releases/fbi-tech-tuesday---building-a-digital-defense-against-the-internet-of-things-iot)

---

### Post by lazaruslong67 on 2023-10-18
> **TheFu said:**
> Sure. Backup the data. Reformat the partition. Copy the data back.  Ensure you get the permissions correct AND don't be lazy with 777.  That's asking to have all the files deleted.
No matter what storage is used, backups are mandatory.  If you don't back up the data, it clearly isn't very important.  

For media, I only have 1 copy, not the normal 3-2-1 method. That's because media files are huge and seldom change. Either they exist or they don't.

BTW, any chance I could talk you out of plex?  Jellyfin is the similar alternative, but 100% F/LOSS and supports a wider range of media types without phoning home every click seen to the Plex guys.  For recording TV OTA, Jellyfin is much better.  The reason to use Plex or Jellyfin is for centralized media. If you only have 1 system to playback media on, then Kodi would be easier.  All of them use the same directory structure, so you can actually run all of them against the same TV shows and Movies and Photos and Music without impacting the others.

There are many things where plex is "slicker", but there are also real privacy failures in Plex. Looking at my network logs back when I ran Plex, only my Roku box tried to phone home more often.  Every damn click was sent.  If you aren't willing to change from Plex, please, please, please, follow the FBI recommendations and put it onto a completely different subnet away from desktops and other computers with important things.  [https://www.fbi.gov/contact-us/field-offices/portland/news/press-releases/fbi-tech-tuesday---building-a-digital-defense-against-the-internet-of-things-iot](https://www.fbi.gov/contact-us/field-offices/portland/news/press-releases/fbi-tech-tuesday---building-a-digital-defense-against-the-internet-of-things-iot)

Have been using Plex for over 10 years now, but have also recently tried both Emby and Jellyfin.  My biggest complaint with JF is the client support.  I use Apple TV and honestly neither they JF Apple TV app (or Emby for that matter) are as polished as the Plex app.

I would definitely consider moving off of Plex once the apps get to a decent enough level though (although that will require getting my small number of family and friends to move as well).

---

### Post by TheFu on 2023-10-19
I don't touch Apple stuff.  They have enough money and don't need any of mine.

I don't really use the JF clients, just the straight DLNA aspect from the server and use Kodi to handle playback.  I find the Jellyfin clients aren't great, especially playback. they put things in odd places and don't allow the control I'm used to.  Kodi does a better job, for my needs.

I'm just very privacy concerned and really dislike having our data stolen without actual compensation.  They should be paying us for our data to get it, not charging us to use a tool that takes it.

A pi4 or pi5 running OSMC (a pi-optimized Kodi) handles non-DRM stiff nicely.

If your family/friends are leveraging your Plex Server and you move, then they will move too. No choice.  The question comes down to how willing you are for the Plex people to have so much access to all your media. Only you can make that decision.  Remote Plex access is easier.  With the other options, if you don't care about security, you'll need to open ports for Jellyfin.  OTOH, if you do care about security, you could setup/run a wireguard VPN server to allow secure access to your LAN for them. Perhaps you run a nextcloud server and everyone shares it?  That's up to you.  Just be certain to keep your internet facing stuff on a different LAN than your IoT stuff and different from your normal desktop stuff.  Security matters these days.

---

