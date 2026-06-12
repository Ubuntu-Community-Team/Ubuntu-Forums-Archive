---
title: "MPlayer not finding my DVD drive"
date: 2004-11-02
forum: General Help
---

### Post by iminj on 2004-11-02
I have 2 optical drives on my system ... one is DVD-ROM; and the other is CD-RW.
I followed the Multimedia HOWTO including adding libdvdcss2 from the debian-marillat repository to enable DVD playback.  

DVD's will not play. Here's what happens:

When I put the DVD in the DVD drive, it mounts, and opens an icon on my desktop.  I checked the properties; it identifies the location as /media/cdrom0. When I open MPLayer, and select DVD > Open Disk ... it returns the following message: "Couldn't open DVD device: /dev/dvd".

There was a line in the HOWTO to link the drive and I followed it exactly as suggessted:

"sudo ln -s /media/cdrom0 /dev/dvd"

Did this command create the problem I now have ... or should I have modified it in some way? Anyone?

iminj

---

