---
title: "HD recovery w/ live cd - read only?"
date: 2007-07-12
forum: General Help
---

### Post by LieToPurify3 on 2007-07-12
My pc says my HD has failed, so I am trying to boot up with my Ubuntu live cd to recover the files.  However, the live cd makes everything "read only"! Is there any way around this so that I can backup my files to an external HD?  I can see my windows files from the cd, and the external HD.  I just need permission.  Thanks!

---

### Post by gentlerain on 2007-07-13
I would suggest to give the "dyne-bolic" Linux distribution a try at [www.dynebolic.org]("http://www.dynebolic.org").

I've been using the dyne:bolic 2.3 DHORUBA release from 11-23-2006.  I've mainly used it as a live CD, but it can also be placed on the hard drive by using a nest (which works well).  Please note that (at least for the 2.3 release)  when you boot from the CD, there are some icons on the Desktop but no panels.  Right-clicking will bring up menus and submenus for the various programs.

I have one IDE hard drive on my system, so after the live CD boot, dyne:bolic places my hard drive in /mnt/hda/1/, the last / being the "/" directory in Ubuntu on the hard drive.  The interesting thing about dyne:bolic is that I have complete access to my hard drive as root.  So I can add, delete, & edit any file in my Ubuntu setup in any users directories- no questions asked.  Although this may be handy in some cases, in another sense it could be a security issue.

Note that when I boot from the Ubuntu 6.10 live CD I could not find the hard drive in the media or mnt directories.  If you know of a way to do this with Ubuntu I would like to know.

Good luck,

Mike

---

### Post by longlegs on 2007-07-13
Hi !

> **LieToPurify3 said:**
> My pc says my HD has failed, so I am trying to boot up with my Ubuntu live cd to recover the files.  However, the live cd makes everything "read only"! Is there any way around this so that I can backup my files to an external HD?  I can see my windows files from the cd, and the external HD.  I just need permission.  Thanks!

If you only want to COPY the files to an external hd, what is your problem? Read-only means that you can read the files in order to WRITE them to the external hd. What else do you need?
OR did you mean that the external hd is read-only? If so, you can change the permissions by right clicking the ext. hd icon and choosing properties. I have found tho that some times you have to do this more than once for it to take effect.
BTW do not install any thing to the damaged hd. and  use it as little as possible until you get your backup made. It is sick now. Too much usage may make it dead.
Good Luck!
longlegs

---

### Post by longlegs on 2007-07-13
Mike, did you check /dev?

longlegs

---

