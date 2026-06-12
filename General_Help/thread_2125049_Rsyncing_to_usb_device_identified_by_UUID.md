---
title: "Rsyncing to usb device identified by UUID"
date: 2013-03-12
forum: General Help
---

### Post by cogset on 2013-03-12
I'd like to rsync my home directory at fixed intervals to an external  usb drive using a cronjob : the issue I'm facing is that I obviously  can't specify the destination directory for rsync using something like  /dev/sdd or the likes,as that external drive won't be plugged it all the  time and that /dev/sdd may refer to another drive at that particular  moment.

I've already set up a system notification as a reminder  to plug in the drive,but even so there's of course no guarantee that the  backup device will be getting that /dev/sdd identification,as other  external devices may be plugged in already.

So I was thinking if  it could be possible to use the UUID of that particular USB drive to  identify it in the crontab,so that the rsync process won't be eventually  write to the wrong device.

---

