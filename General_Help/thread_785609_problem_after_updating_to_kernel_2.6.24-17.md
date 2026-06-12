---
title: "problem after updating to kernel 2.6.24-17"
date: 2008-05-07
forum: General Help
---

### Post by vrhahaha on 2008-05-07
The story goes like this, I was curious about the high CPU usage whenever i open firefox and decided to look for a fix. Stumbled upon the page

[https://bugs.launchpad.net/firefox/+bug/215728](https://bugs.launchpad.net/firefox/+bug/215728)

and try the fix suggested which is to update to the 

xulrunner-1.9 version 1.9~b5+nobinonly-0ubuntu4~8.04.0mt1

after i updated and restarted. Now the problem started as the processor's fan start running at full speed. And i check my system monitor to find out strange cpu activities (see attachment) even without any programs running.

Any suggestion of how to find the problem, or how to fix this?
Any help would be much appreciated.

Cheers

---

### Post by Tom--d on 2008-05-07
In the processes tab, what is using the CPU?

---

### Post by vrhahaha on 2008-05-07
checked the system monitor, and the cpu still exhibiting the same behaviour as the attachment in my 1st post.

the screenshots for processes tab are attached

edit:*bump*

---

### Post by vrhahaha on 2008-05-09
*bump*

---

### Post by yaknowwat on 2008-05-09
thats normal the system monitor in ubuntu can be a resource hog.

Open a terminal and type in this to get a more efficient monitor
```
top
```
add " --help" for options.

---

### Post by vrhahaha on 2008-05-10
i followed ur suggestion and found that it's the system monitor that's causing the abnormal usage.

However i am still quite curious why this happened after the update. Prior to that, i didn't see such behaviour. Any suggestion?

Thanks for your reply.

---

