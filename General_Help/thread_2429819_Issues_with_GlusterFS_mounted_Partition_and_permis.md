---
title: "Issues with GlusterFS mounted Partition and permissions"
date: 2019-10-23
forum: General Help
---

### Post by henrik-andersson on 2019-10-23
Hey!

This is my first post here at the forum. I have used it for quite a while but today I had to actually register so I could write about my issues.

I run a glusterfs-server on 3 of my servers at home, and between those 3 servers I run a glusterfs-partition which is replicated over all three servers.
I can mount it and everything, but when I try to set permissions to 0644 -R /mnt/partition/ 
and then try to use any video files on the partition, VLC tells me that it can't play the file(s), and it also adds an "admin:///" before the absolute file path.
If I set the permissions to 744 or even 700 I can use the files in VNC as much as I want, no problems at all.
(Oh yeah, the user:group on the /mnt/partition/ is myuser:myuser on entire partition and with myuser I mean the username:group I use on my workstation where U try to play the files in VLC).

I thought you could at least use video-files with permissions 644 at least, I did'nt think they had to be 7** to be able to just play the files in VLC.
Is there anyone who knows why this is?
Is this really correct the way this works for me on my glusterfs partition?

I have used linux on my workstations for arount 4-5 years and also on my 8 servers for equal amount of time, so I'm not totally n00b when it comes
to Linux / Ubuntu.

Please help me or at least let me know if this is as it should be, or if there's something weird about my "issues".

P.S I'm running Ubuntu 18.04 on both workstations and on my servers.
I have tried with both VLC 4.0.1 and VLC 3.7.0 but it's the same on both.


Best Regards
Henrik Andersson

---

