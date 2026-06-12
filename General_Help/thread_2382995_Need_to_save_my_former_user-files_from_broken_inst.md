---
title: "Need to save my former user-files from broken install via Live-OS: &quot;no read-access&quot;"
date: 2018-01-19
forum: General Help
---

### Post by soulflight on 2018-01-19
Hello everyone,

I had a huge problem that destroyed my existing kernels on an Acer Aspire ES1 Netbook. The HDD was fully encrypted and when trying to upgrade from 14.04 to 16.04, the machine froze. Forced to hard-reset, I ended up with a very broken installation that gave me kernel panic when trying to access both normally as well as recovery mode.
Since I see no hope in saving my existing installation, I want to reinstall and copy over my user folder items to keep all my app data and files.

I can mount my encrypted HDD partition in the Live-System of 16.04 without any problems, but some of the files and folders in there are marked with an X and "insufficient rights" prevent me from opening them or copying them over. As far as chkdsk and a scan for bad sectors told me, the partition is healthy.

How can I make the user specific files in my user folder accessible when using a Live-System?

---

### Post by DuckHook on 2018-01-19
Welcome to the forums, soulflight.

Wish you were here under better circumstances.

As I understand it, you've successfully mounted the old HDD and also successfully decrypted it. So, the most serious roadblocks have been cleared.

When you run a LiveUSB, it runs as root with a special UID of 999 (I believe). However, when you installed, your personal UID would have been 1000. That's the default for all of the *buntus. Since Linux is a secure OS that enforces permissions, your old files under /home (UID 1000) will not be accessible for reading or writing to your LiveUSB user (UID 999) unless you originally set those permissions to allow reading and writing for "others". Root-owned files are another matter. Many system files owned by root do not permit access to anyone but root. However, the standard root user (not the special one in a LiveUSB) is UID 0. Therefore, your LiveUSB root user won't be able to access those either.

You shouldn't have any root-owned files in /home. If you do, then you did something naughty. In any case, you should be able to copy everything from /home to another backup media without problem. If some things won't copy, then look at the file permissions. You may have to either change those permissions or change your user in the LiveUSB.

---

### Post by DuckHook on 2018-01-19
This is a tangent, but worth mentioning&#8230;

Many gurus on this forum, including buddies of mine, are big on whole-disk encryption. I've never been comfortable with it. Of course, if you have highly sensitive data on your machine, then whole-disk is unavoidable, but for general users, it's overkill. And it leads to drawbacks like the one you are going through now. You were lucky and were able to mount, then decrypt your drive. That's not always possible, especially if certain key areas of the drive get corrupted or fail. When you re-install, you may wish to consider encrypting more selectively&#8212;perhaps only a "Private" directory in /home, moving all of your sensitive stuff into that, then symlinking back to where the system expects to find it (that's my practice).

Last but not least, I hope this unfortunate episode has reinforced the lesson expressed in my sig and you will practice rigorous backups from now on.

---

### Post by soulflight on 2018-01-19
> **DuckHook said:**
> Welcome to the forums, soulflight.

Wish you were here under better circumstances.

As I understand it, you've successfully mounted the old HDD and also successfully decrypted it. So, the most serious roadblocks have been cleared.

When you run a LiveUSB, it runs as root with a special UID of 999 (I believe). However, when you installed, your personal UID would have been 1000. That's the default for all of the *buntus. Since Linux is a secure OS that enforces permissions, your old files under /home (UID 1000) will not be accessible for reading or writing to your LiveUSB user (UID 999) unless you originally set those permissions to allow reading and writing for "others". Root-owned files are another matter. Many system files owned by root do not permit access to anyone but root. However, the standard root user (not the special one in a LiveUSB) is UID 0. Therefore, your LiveUSB root user won't be able to access those either.

You shouldn't have any root-owned files in /home. If you do, then you did something naughty. In any case, you should be able to copy everything from /home to another backup media without problem. If some things won't copy, then look at the file permissions. You may have to either change those permissions or change your user in the LiveUSB.

Exactly, when i open my former user-folder in the file manager of the Live-System, some files and folders are marked with a grey X-symbol in the lower right corner of the icon. The pattern seems pretty random, often in the same directory there are accessible files and forbidden files. Opening the access-rights tab of properties on one of those denied-access-files shows UID 1000 as the owner of the files. 

So how do i become User 1000 in LiveUSB?

---

### Post by DuckHook on 2018-01-19
Just create a new user using User Accounts (I assume you are using Ubuntu Xenial LiveUSB?). The first user you create will have UID 1000. Make sure you create it with exactly the same name and password you had before. Make sure you make this user an administrator. Then logout&#8594;login as new user. You should now be able to access all of your old files.

---

### Post by soulflight on 2018-01-20
Of course :lolflag: copying the folder now, so it worked. ;) thanks

---

### Post by DuckHook on 2018-01-20
You're welcome. Glad it all worked out.

Good Luck and Happy Ubuntu-ing!

---

