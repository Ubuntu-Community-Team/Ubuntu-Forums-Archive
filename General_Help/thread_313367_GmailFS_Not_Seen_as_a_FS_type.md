---
title: "GmailFS Not Seen as a FS type"
date: 2006-12-05
forum: General Help
---

### Post by Adanufgail on 2006-12-05
I followed all the tutorials I could find, and still can't fix this.

```
sudo mount -t gmailfs /usr/share/gmailfs/gmailfs.py /media/gdrive -o username=*****,password=*****,fsname=******
mount: unknown filesystem type 'gmailfs'
```

Any help would be greatly appreciated,
Micahel Lubert

---

### Post by WorLord on 2006-12-06
Sounds like you didn't configure/recompile the kernel with gmailfs, or you compiled it as a module.  (If you're planning to boot from it, you really should have it statically compiled into the kernel, not compiled as a module.)

Assuming you're not booting from it, and want to mount a gmailfs filesystem after you're booted, you could then use the module to do so, but you'd have to make sure it's loaded every boot.

---

### Post by Adanufgail on 2006-12-06
I'm not booting from it.
How would I go about loading it?

---

### Post by onegreenparker on 2007-07-25
Good Question.....
Any ideas?

---

