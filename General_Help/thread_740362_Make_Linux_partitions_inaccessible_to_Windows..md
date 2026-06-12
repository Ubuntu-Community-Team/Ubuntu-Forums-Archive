---
title: "Make Linux partitions inaccessible to Windows."
date: 2008-03-30
forum: General Help
---

### Post by Kemono on 2008-03-30
Is there a way I can make the Linux partitions inaccessible to Windows? I mean, I know that by default Windows can not see the Linux partitions, but if you install Ext3 drivers, it will. So, what's the magic trick I need to do to make sure it's impossible (or at least very hard) for Windows to see the Linux partitions? If also possible, I don't want them to be visible in Disk Management.

One more question: If one decides to reinstall Windows, is there a way to prevent them from formatting the Linux partitions?

Off-topic question: Where can I see my video memory? I posted this question [ [COLOR="DarkOrange"]here[/COLOR] ](http://ubuntuforums.org/showthread.php?t=737182) but no one answered it.

Have a good day. Or evening. Or whatever you're having.

---

### Post by pseudo-random on 2008-03-30
If you're looking for security then encrypt the entire partition with trucrypt. Plenty HOWTO's out there on how to do it. You'll need another partition to host the trucrypt program though.
No-one will be viewing data in that partition then.

---

### Post by Kemono on 2008-03-30
Looks tricky. Will look into that when I see some daylight, as it's a little late right now. Thanks!

---

