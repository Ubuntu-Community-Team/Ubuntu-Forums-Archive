---
title: "[SOLVED] Tyding things up"
date: 2007-08-20
forum: General Help
---

### Post by Kowalski_GT-R on 2007-08-20
hello,

I just managed to understand how to mount my second physical HD in Ubuntu.

This link ([http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")) and O'Reilly's guide helped a lot.

Still, it took me three tries before it clicked.

Now I have two nasty directories in Filesystem with /root Permissions which I want to remove.

/etc/fstab is now edited correctly,

whats the correct command to code?

thanks,

Andre

---

### Post by kellemes on 2007-08-20
> **Kowalski_GT-R said:**
> hello,

I just managed to understand how to mount my second physical HD in Ubuntu.

This link ([http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")) and O'Reilly's guide helped a lot.

Still, it took me three tries before it clicked.

Now I have two nasty directories in Filesystem with /root Permissions which I want to remove.

/etc/fstab is now edited correctly,

whats the correct command to code?

thanks,

Andre

Maybe I'm not understanding.. but.. you simply want to remove two directories with root-permissions?
From terminal do..
sudo rm -r /path/to/directory

---

### Post by Kowalski_GT-R on 2007-08-20
thank you,

it really was as simple as that.
cheers,

Andre

---

### Post by southernman on 2007-08-20
Werd to the wise... be very carful with that command.

I recently lost all my music and movies after running the command on a box I was sshed into, not thinking that I had setup a shared folder on the machine sshing from.... I watched in great pain as all my media files went POOF. You can't kill the process fast enough!

I literally banged my head on the keyboard saying "Stupid Stupid Stupid!" Dozens of hours of work just vanished in an instant.

---

### Post by kellemes on 2007-08-20
> **southernman said:**
> Werd to the wise... be very carful with that command.


Can't be said often enough..
For some reason we (people) need to crash first and learn later.. :popcorn:

---

