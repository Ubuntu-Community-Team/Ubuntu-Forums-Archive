---
title: "chroot, getting back to host"
date: 2007-11-02
forum: General Help
---

### Post by picopir8 on 2007-11-02
I am setting up a custom liveCD with all repository updates.  I have extracted the livecd into a directory and then chroot-ed into that directory to apply all the updates.  It works fine, but it is time consuming to download all of the updates and install the packages that I want.

What I would rather do is use my local repository archive.  That is stored on a USB drive but once I chroot into the livecd directory I loose visibility to everything outside of that directory.  I tried setting up a link (though I did not think it would work), and as I suspected, it did not work.  Any ideas?

---

### Post by bingoUV on 2007-11-02
> **picopir8 said:**
> I am setting up a custom liveCD with all repository updates.  I have extracted the livecd into a directory and then chroot-ed into that directory to apply all the updates.  It works fine, but it is time consuming to download all of the updates and install the packages that I want.

What I would rather do is use my local repository archive.  That is stored on a USB drive but once I chroot into the livecd directory I loose visibility to everything outside of that directory.  I tried setting up a link (though I did not think it would work), and as I suspected, it did not work.  Any ideas?

Maybe you know this, but you can just exit from the chroot environment to get back.

For doing it within chroot, you could use a sshfs to the same computer, mount it inside the chrooted environment, and access the stuff outside chroot jail.

---

### Post by picopir8 on 2007-11-02
Yep, I wanted to stay within chroot so the apt-gets only work on the liveCD image and not the host computer where I am doing the development.

I did change the mount path of my USB drive to be somewhere within the chroot directory and it was accessible but I I would prefer not to move my mount points around.  sshfs looks promising so I will give that a try.  Thanks.

---

