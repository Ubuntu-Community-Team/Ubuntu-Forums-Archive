---
title: "Mount and Create Symbolic Link to WD My Book Live NAS"
date: 2013-03-03
forum: General Help
---

### Post by mark2741 on 2013-03-03
Been struggling with this for a week now. I've tried numerous things but cannot get this NAS to be visible to applications (specifically, a media server such as Plex or XBMC).

The requirement is for the directories on the NAS to auto-mount on startup of Ubuntu, and also be symbolically linked (I believe that's the term) to a folder in my home directory. The reason for the link requirement is because I will then need to set ownership and permissions as needed for the Plex Media Server (or any other application) to be able to 'see' the directories on the NAS.

I already can see the NAS directories just fine via Nautilus - that worked out of the box. The problem is that Plex nor XBMC can see/browse to the directories. 

My latest attempt at fixing this was to create an /etc/fstab entry like this:

#Entry for WD NAS Media
/192.168.1.5/Media /home/mark/NETWORK_SHARED smbfs username=admin,password=XXXXXX 0 0

My hope was that this would mount the Media directory contained on the NAS, to the NETWORK_SHARED directory in my home folder (it's already created).

The WD My Book Live NAS is formatted for ext4 per Western Digital. I have tried "auto", "cvfs", "smbfs", and "ntfs" and none of those mount parameters work in fstab. On another forum I kept getting told that it was a gvfs drive and that I have a .gvfs directory in my home folder that it would show up in, but there is no .gvfs directory in my home folder (I have enabled showing hidden files and it still doesn't show).

Any help with this will be greatly appreciated! I feel like I wasted $160 on this drive : ( The other alternative will be having to go back to using OS X for my primary OS, which I do not want to do.

---

