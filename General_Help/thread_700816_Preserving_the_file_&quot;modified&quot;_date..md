---
title: "Preserving the file &quot;modified&quot; date."
date: 2008-02-18
forum: General Help
---

### Post by e_james on 2008-02-18
I would like to transfer most of my computer activity from Windows to Linux but there are some differences in the way the two systems work. I can learn to live with most of these but I have recently come up against a real deal-breaker. As far as I can discover, Linux / Unix users see the file "modified" date as much less important than Windows users do. I currently have around 2.6TB of files on the hard drives of my video editing PC. My entire file management and backup strategy depends on the "modified" date/time. 

I have been looking at some file synchronising software and found two good candidates - "AllwaySync" for Windows and "Unison" for Unix and Windows. The difference in their behaviour highlights the problem. Unison apparently compares files on the basis of name and content. The setup procedure can take hours. AllwaySync appears to compare files on the basis of name, size and modified date. The setup completes in less than a minute. When AllwaySync copies a file, it preserves the modified date. When Unison copies a file (even in Windows), it sets the modified date/time to the moment of copying.

When I discovered this situation I did some additional tests. It seems that many of the linux file copying procedures use rsync or a similar technique. Because of the way rsync works, the obvious end result is that the modified date of the destination file becomes now. I am thinking that it doesn't have to be that way but the concept is so much a part of linux thinking that most users would not care - hence Unison. Unfortunately I do care. If I can't find a way around this obstacle, linux can never be more than a minor interest for me.

One possible Linux synchronising strategy might be to use Windows to do it. Another might be to write my own copying / synchronising software.

Any comments / suggestions?

---

