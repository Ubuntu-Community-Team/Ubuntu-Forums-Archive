---
title: "[SOLVED] Trashed permissions"
date: 2008-07-06
forum: General Help
---

### Post by SkonesMickLoud on 2008-07-06
Through an attempted dual-boot install of XP, I ended up screwing my MBR.  I could access all of my files through the LiveCD, so I copied my /home to an external HDD, formatted the entire internal HDD, and reinstalled Ubuntu.  When I finished the install, I overwrote the /home on my internal with the /home from my external.

Now the permissions are wrecked.  I don't own anything, and I can't write, or execute anything.  I seem to have gotten to the point where I can see all of the directories and files in /home, but nothing inside of any of the sub-dirs.

When I log in, it tells me to change the permission of ~/.dmrc to 644, but this does nothing.

Ideas?

---

### Post by sdennie on 2008-07-06
Try booting into recovery mode selecting the root shell option and doing:

```

chown -R your_username:your_username /home/your_username

```

Obviously, replace "your_username" with your username.  :)

---

### Post by SkonesMickLoud on 2008-07-06
No change.

The error I receive when I log in:

User's $HOME/.dmrc file is being ignored.This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  Users $HOME directory must be owned by user and not be writable by other users.

---

### Post by sdennie on 2008-07-06
When you made your backup, did you do a raw "cp" or did you use something like "tar"?  If you used "cp", the permissions on your files were not preserved.  That's not catastrophic for the most part but, some applications will not be pleased about it.  To fix the problem you are currently having, just run:

```

cd
chmod -R 0755 .
chmod 0644 .dmrc

```

That will reset all files to default permissions and then change .dmrc to what it wants to be.  You may find other files that are unhappy about being 0755 but, you can change those on a case by case basis.

---

### Post by SkonesMickLoud on 2008-07-06
Now it won't let me log in at all, and I cannot sudo in a virtual terminal.

I'm going to move a select few files from the internal to the external and reinstall.

Thanks for the try.

---

### Post by sdennie on 2008-07-06
Before re-installing, try booting into recovery mode from grub.  From there, you should be able to get a root shell and move to /home/your_username and run the commands I mentioned above.  After that, type "exit" and select resume and see if your problem is fixed.

---

### Post by SkonesMickLoud on 2008-07-06
> **vor said:**
> Before re-installing, try booting into recovery mode from grub.  From there, you should be able to get a root shell and move to /home/your_username and run the commands I mentioned above.  After that, type "exit" and select resume and see if your problem is fixed.

That's what made it unbootable.  For some reason.

But I'll give it another shot.

---

### Post by johnystevenson on 2008-07-12
hi there

i have the same error message although i arrived there from a different reason, so would like to know how yoo get on

regards
johny

---

### Post by SkonesMickLoud on 2008-07-12
I ended up doing a clean wipe with reinstall.

I kept my /home files relatively intact by booting into the LiveCD and moving my entire /home over to an external HDD.  Then, while my files were on the external, I followed vor's instructions from post #4, then created a tar archive of the files I wanted to keep and moved them back to my new /home after I reinstalled.

It might not be the best way to do it, but I was being impatient, and it ended up working.  I'd try vor's method before trying mine.

---

