---
title: "Making a file server, need some help"
date: 2012-10-27
forum: General Help
---

### Post by incindre on 2012-10-27
Hi all,

I've bought a machine to use as a file server running Ubuntu Server  12.04 and have been tinkering for a week now but meet problems at every  step.
I'm pretty sure I'll format and do a fresh install after I've sussed out  how to get things working, but it's a painful process and I need some  help.

If someone can tell me briefly what I'd need to do to get this functionality:


[LIST]
[*]A RAID10 array hosting all the user specific data for two local  Windows 7 Machines (by that I mean, I want to be able to click on  'libraries' on either PC and seamlessly be directed to the respective  documents, downloads, music, videos & pictures folders hosted on the  server).
[/LIST]



[LIST]
[*]A second shared folder specifically for media which would be  accessed from every user on the Win 7 machines (both have the same  users) and from my WDTV Live (which does support Samba).
[/LIST]


I manage my server using ssh and Webmin and have created my raid array through the latter.
 I need to know things like: if the current file system (ext4) works  with the windows machines happily, or if I need to format in NTFS. How  to configure Samba (preferably through Webmin) to give me the  functionality I need etc. Currently the Samba shares show up but I can't write to them from the W7 machines.


Thanks in advance!

---

### Post by incindre on 2012-10-27
Shameless self bump.

---

