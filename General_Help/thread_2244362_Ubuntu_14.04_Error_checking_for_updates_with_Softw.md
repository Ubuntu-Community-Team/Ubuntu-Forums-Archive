---
title: "Ubuntu 14.04 Error checking for updates with Software Updater"
date: 2014-09-15
forum: General Help
---

### Post by hockeybum27 on 2014-09-15
Ubuntu 14.041 (upgrade from 12.04) 64 bit

A couple of weeks ago I started to get a warning icon in the upper-right corner (I'd call it the system tray if it was another OS) for Software Updater.  When I try to check for updates, I get:

> W:Failed to fetch [http://download.tuxfamily.org/glxdock/repository/ubuntu/dists/trusty/cairo-dock/binary-amd64/Packages](http://download.tuxfamily.org/glxdock/repository/ubuntu/dists/trusty/cairo-dock/binary-amd64/Packages)  404  Not Found [IP: 88.191.250.18 80]
, W:Failed to fetch [http://download.tuxfamily.org/glxdock/repository/ubuntu/dists/trusty/cairo-dock/binary-i386/Packages](http://download.tuxfamily.org/glxdock/repository/ubuntu/dists/trusty/cairo-dock/binary-i386/Packages)  404  Not Found [IP: 88.191.250.18 80]
, E:Some index files failed to download. They have been ignored, or old ones used instead.

When trying to install the latest Ubuntu security updates I get:

> An attempt to commit /etc changes to bzr failed.
You may manually resolve the issues with the uncommitted changes before continuing.

This was a 12.04 that I upgraded to 14.04 about 6 weeks ago; I did not have problems with this until about 2 weeks ago.

Thoughts?  Next steps?

Thanks in advance!

---

### Post by Bashing-om on 2014-09-15
hockeybum27; Hi !

Seems that " http://download.tuxfamily.org/glxdock/repository/ubuntu/dists/trusty/cairo-dock/binary-amd64/Packages"
Is not supported in 'trusty' ; per:
[http://download.tuxfamily.org/glxdock/repository/ubuntu/dists/](http://download.tuxfamily.org/glxdock/repository/ubuntu/dists/)
As there is no listing for 'trusty'.

Disable the source and try to update/upgrade once more.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by hockeybum27 on 2014-09-16
Bashing - Hi and thanks for the quick reply!

I'd actually thought I'd done that a while back, but when I checked, it was still there!  I will check this and confirm if it resolves the issues; so far, so good - I ran 'check for updates' and got no errors.
FMI - how do I remove that entry from the list (rather than just un-check it)?  I see an entry in sources.list for it, but it's commented out - would I just remove it altogether from there?

Thanks!

Chuck (hockeybum27)

---

### Post by slickymaster on 2014-09-16
> **hockeybum27 said:**
> <...snip...>
FMI - how do I remove that entry from the list (rather than just un-check it)?  I see an entry in sources.list for it, but it's commented out - would I just remove it altogether from there?

Thanks!

Chuck (hockeybum27)

Open "Software Center" and navigate to Edit > Software Sources. There go to tab "Other Software", choose the entry and press the "Remove" button.

---

### Post by hockeybum27 on 2014-09-16
Thanks to both SlickyMaster and Bashing-om!
Each of you answered one part of my question(s), I normally would have seen the issue reported again by now if it weren't solved, so I am marking it as solved.

Again many thanks to you and all who answer here - some day I hope to be able to contribute as well.

Chuck

---

### Post by Bashing-om on 2014-09-16
hockeybum27; Great !

Pleased it has all worked out.
Contributions to this effort that is our operating system by choice; There are many ways:
[http://ubuntuforums.org/showthread.php?t=2244263](http://ubuntuforums.org/showthread.php?t=2244263)
We can use all the help we can get.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]All for 1
[INDENT][INDENT][INDENT]and one for all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

