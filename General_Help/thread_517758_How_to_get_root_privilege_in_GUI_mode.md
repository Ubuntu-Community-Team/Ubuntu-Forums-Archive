---
title: "How to get root privilege in GUI mode"
date: 2007-08-04
forum: General Help
---

### Post by jutirain on 2007-08-04
I have an external hard drive that in ext3 format.

The system can detect it correctly, however, it is set to be read only.
(I used gparted to format it from fat to ext3)

I want to set the privilege in Nautilius by right click on the label of the HD and choose "Properties" -> "Permission" tab, however, it will output error message "The permission could not be changed", which may due to the lack of root privilege.

I've tried "gksudo nautilius", but no help.

So, how can I get root privilege in GUI mode?

Or how can I change the permission of the HD in command line mode?

Thanks a lot!

---

### Post by merlinus on 2007-08-04
```

gksudo nautilus

```

-merlin

---

### Post by The Wisedude on 2007-08-04
I use "Sudo Nautilus"

---

### Post by merlinus on 2007-08-04
Best to use

gksudo

for graphical apps.

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

-merlin

---

### Post by jutirain on 2007-08-04
I've tried "gksudo nautilius" & "sudo nautlius", no helps either. :(

Any idea to change the permission in command line mode?

---

### Post by merlinus on 2007-08-04
You are spelling nautilus incorrectly.  Best to copy-and-paste commands from posts.

-merlin

---

### Post by jutirain on 2007-08-04
Yeah, you're right.

However, the nautilus is different from the ordinary user mode?

I click on the "Computer" and I can't see the hard drives and cdroms originally there...

---

### Post by merlinus on 2007-08-04
Your drives and partitions are in FileSystem/media.

-merlin

---

### Post by jutirain on 2007-08-05
Done!

Thanks a lot :)

---

