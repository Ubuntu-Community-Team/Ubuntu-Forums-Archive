---
title: "I need help with my iPod"
date: 2007-01-28
forum: General Help
---

### Post by ubageek on 2007-01-28
I am fairly new to Linux and I run Xubuntu on an old Compaq Armada Laptop:D  and it works great but there are still thing that I need help with. The most important to me at this moment is getting my iPod to work with Xubuntu. Well, that isn't strictly true, I mean I have the iPod working with Rhythmbox, but it won't play my m4p files. I have also used Amarok but I get the same result. Is there anyone who can help? 

Another problem I have is that I have Xmms and I found it was a great media player but again I can't get it to play m4p. :mad:

---

### Post by ynnhoj on 2007-01-28
[https://help.ubuntu.com/community/RestrictedFormats/AAC](https://help.ubuntu.com/community/RestrictedFormats/AAC)

have you installed the gstreamer0.10-plugins-bad-multiverse package?  you may need to enable the multiverse repository..

as for xmms: i'm not sure whether or not an aac/mp4 plugin exists for it.  you'll have to look through the list of packages in synaptic, or do a bit of googling. [edit: a quick search turned up the xmms-mp4 package, which is also in the multiverse]

---

### Post by ubageek on 2007-01-28
Hey Dude, thanks for the help with xmms the new plugin works great, but I still have the problem with rhythmbox, I did "sudo apt-get install gstreramer0.10-plugins-bad-multiverse"
and it went through all the install but how can apply it to rhythmbox because it still won't play :confused:

I know this is a pretty noob question but I'm new and am willing to learn:lolflag: 

Again thanks for the help with xmms.

---

