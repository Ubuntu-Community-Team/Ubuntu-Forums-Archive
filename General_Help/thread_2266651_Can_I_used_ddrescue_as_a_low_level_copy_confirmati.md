---
title: "Can I used ddrescue as a low level copy confirmation tool"
date: 2015-02-24
forum: General Help
---

### Post by joeslide on 2015-02-24
I am copying a file from one security domain to another. The transfer is done with a CD/DVD. I need to make sure that when I copy the file(s) to the CD/DVD that nothing else is copy along with it. Can I use ddrescue as a confirmation tool in this process? If so, what options should a use on the command line?

Thanks,
joeslide

---

### Post by TheFu on 2015-02-25
A byte count is hardly verification.  I'd use par2 and md5 and sha1 checks. Certainly there is a process documented for this in your environment. Follow that. Don't make something up.

---

