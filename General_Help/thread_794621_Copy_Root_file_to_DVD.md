---
title: "Copy Root file to DVD"
date: 2008-05-14
forum: General Help
---

### Post by screaminfakah on 2008-05-14
Hello, 
I followed a tutuorial in this forum on how to create a compressed backup (.tgz).  It saved the backup in the root directory but the tutorial didn't explain how to access this file to burn it to DVD.  I would like to copy it to DVD and then dump the backup to conserve space on the drive. 
Im still learning how to navigate Ubuntu. 
Thanks,

---

### Post by Joeb454 on 2008-05-14
In the root directory as in / ?

If so open a terminal (Applications > Accessories > Terminal) and run ```
sudo cp /<backup name>.tgz ~/Desktop/
``` and that will place it on the desktop. Note that you will be asked for your laptop, but it will show no input. Rest assured that your password is being entered :)

You should have permission to write it to a dvd from there. Ubuntu comes with Brasero by default, which is pretty good for things like that, it's in Applications > Sound & Video

Despite it's menu location, it can do more than audio cd's etc. :)

---

### Post by screaminfakah on 2008-05-14
Thanks, I will try that.
Now will the original file still be in the root or does it completely move it to the desktop?  I would like to delete it after I burn it to save space.

---

### Post by Joeb454 on 2008-05-14
Oh that will just copy it, and leave it there, the following will move it to your desktop (from root).

```
sudo mv /<filename>.tgz ~/Desktop/
``` it keeps the same filename when you move it too :)

---

### Post by screaminfakah on 2008-05-14
Perfect.  Thanks Again!

---

### Post by Joeb454 on 2008-05-14
No worries, glad it worked :)

---

