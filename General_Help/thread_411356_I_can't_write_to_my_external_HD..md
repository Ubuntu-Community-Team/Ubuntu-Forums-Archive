---
title: "I can't write to my external HD."
date: 2007-04-16
forum: General Help
---

### Post by Error47 on 2007-04-16
I have a firewire external Hard Drive. I can read files from it, but I cannot save files on it.  It just tells me " You do not have permissions to write to this folder. " What can I do?

---

### Post by raffytaffy on 2007-04-16
chmod 777 /path/to/drive

chroot user /path/to/drive

u can also have it auto mount on start up if u add it to your fstab with "defaults" 0 0

---

### Post by Error47 on 2007-04-16
No that doesn't work. Sorry I failed to mention, it's NTFS...

---

### Post by Maestro23 on 2007-04-16
ntfs-3g: [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

*Read/Write on NTFS drive.  I'ts in the repositories as well.

---

### Post by hikaricore on 2007-04-16
Just FYI.  Ubuntu linux does not install ntfs writing by default as it is still "experimental".
I've personally never had any trouble but it's for the end user's safety.  If they choose
to install it after Ubuntu, then it's their own responsibility.

---

### Post by Error47 on 2007-04-25
Can someone please explain how to use this program? I think I already have it because I was able to write to my that drive before. I dont remember what I did, or if I still have the program. I don't know what to try.

---

### Post by strabes on 2007-04-25
[http://www.ntfs-3g.org/index.html#installation](http://www.ntfs-3g.org/index.html#installation)

---

