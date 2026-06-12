---
title: "can't access tty after removing Dash"
date: 2007-03-09
forum: General Help
---

### Post by General Moskovich on 2007-03-09
I did something quite dumb...removed dash and didn't link sh to bash before hand. Now my system won't boot and just stops in BusyBox with the error:

/bin/sh: can't access tty; job control turned off. 

I'm running edgy for what it's worth. Thanks in advance for any help!

-Sean

---

### Post by scxtt on 2007-03-09
boot a live cd, mount the drive and create the link to bash ...

edit: well at least each of us (on our own) aren't the only one w/ that crazy idea :p

---

### Post by nanotube on 2007-03-09
boot from livecd, mount the disk, create the symlink to bash, then reboot. :)

edit: bah, you beat me to it, scxtt! ;)

---

### Post by General Moskovich on 2007-03-09
Hmmm...I guess that wasn't the real problem. It still doesn't want to boot. Is there anyway to reinstall dash from a live CD? Or is something else all together wrong here?

Thanks!

Sean

---

