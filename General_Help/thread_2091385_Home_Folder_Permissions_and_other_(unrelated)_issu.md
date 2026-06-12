---
title: "Home Folder Permissions and other (unrelated?) issues..."
date: 2012-12-05
forum: General Help
---

### Post by svtguy88 on 2012-12-05
Okay...

Typically my Linux installs work pretty much flawlessly, however, I'm having some issues with my main desktop box.  It also happens to be a development machine, so it tends to get messed with quite often, which may or may not explain some of my issues.

[B][I]_Some background info. . ._
[/B][/I]
**1:  **  On boot, I sporadically see an error about /tmp not being ready.  It gives me the option to wait or skip it.  Typically, I'll hit "wait," and come back in a few minutes and find my desktop waiting for me.

**2:  **  Also, I occasionally see a message on boot about errors being found on my hard drive.  It asks whether to fix them or ignore.  I usually say "fix" and it will sit for a minute, reboot and then work fine (or give me the above "/tmp" error).

**3:  **  Lastly, a lot of programs (Eclipse, Spotify and web browsers) were throwing errors that seemed very deeply tied to the permissions problems.  As it turns out, my home folder permissions got fudged up somehow.  Going to my home folder, doing a right-click, properties and then the permissions tab shows that I don't have read/write access to the files in my home folder -- and if I try to set the "File Access" drop down to read/write and then click "Apply to Enclosed Files," it doesn't do anything at all.

I tried to "chown" my home folder back to me, and then "chmod 700 -R" it to fix things, but I get a bunch of errors about it being a read-only file system.

***Whew***...Sorry, I feel like I'm writing a book here, but I just don't know what to make of my problems.  I'm thinking that the boot-up errors somehow relate to my permissions problems, but I'm not exactly sure how.

---

### Post by rnerwein on 2012-12-05
> **pkmgarf said:**
> Okay...

Typically my Linux installs work pretty much flawlessly, however, I'm having some issues with my main desktop box.  It also happens to be a development machine, so it tends to get messed with quite often, which may or may not explain some of my issues.

[B][I]_Some background info. . ._
[/I][/B]
**1:  **  On boot, I sporadically see an error about /tmp not being ready.  It gives me the option to wait or skip it.  Typically, I'll hit "wait," and come back in a few minutes and find my desktop waiting for me.

**2:  **  Also, I occasionally see a message on boot about errors being found on my hard drive.  It asks whether to fix them or ignore.  I usually say "fix" and it will sit for a minute, reboot and then work fine (or give me the above "/tmp" error).

**3:  **  Lastly, a lot of programs (Eclipse, Spotify and web browsers) were throwing errors that seemed very deeply tied to the permissions problems.  As it turns out, my home folder permissions got fudged up somehow.  Going to my home folder, doing a right-click, properties and then the permissions tab shows that I don't have read/write access to the files in my home folder -- and if I try to set the "File Access" drop down to read/write and then click "Apply to Enclosed Files," it doesn't do anything at all.

I tried to "chown" my home folder back to me, and then "chmod 700 -R" it to fix things, but I get a bunch of errors about it being a read-only file system.

***Whew***...Sorry, I feel like I'm writing a book here, but I just don't know what to make of my problems.  I'm thinking that the boot-up errors somehow relate to my permissions problems, but I'm not exactly sure how.

this looks like you have only one partiton for your ubuntu ( no extra for /home ....)
have a look in your fstab and there you will see the option errors=remount-ro
check your /var/log/syslog and /var/log/kern.log for errors about your disk.
maybe it will help you do boot from CD and run fsck on the disk.
good luch

---

