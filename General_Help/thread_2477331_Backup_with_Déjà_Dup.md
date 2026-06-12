---
title: "Backup with Déjà Dup"
date: 2022-07-21
forum: General Help
---

### Post by ubontik22 on 2022-07-21
Hello everybody,

When I try to backup with Déjà Dup I get a message:
> GPGError: GPG Failed, see log below:
===== Begin GnuPG log =====
gpg: packet(1) with unknown version 185
===== End GnuPG log =====
I searched on the Internet and found this [https://unix.stackexchange.com/questions/532845/how-can-i-fix-this-gpg-error-with-backup-deja-dup-duplicity](https://unix.stackexchange.com/questions/532845/how-can-i-fix-this-gpg-error-with-backup-deja-dup-duplicity).
But I don't have that file
```
~/.gnupg$ ls
private-keys-v1.d  pubring.kbx  random_seed  trustdb.gpg
```

Please help.

---

### Post by TheFu on 2022-07-24
I've read this post 3 times. Just wanted you to know that.  I haven't any clue as I don't use the same tool or any in the family. I'm a little surprised that nobody else has responded since this is the default backup application for the Gnome version of Ubuntu.

Lacking any knowledge specific to the tool (I did look at Duplicity 10 yrs ago), I can only suggest that you purge it and remove all personal settings for it, then reinstall and try again, following the setup instructions.

Looks like deja dup is distrubuted by default as a snap package, which normally would add all sorts of other problems - like not being able to access all files on the OS, but a backup tool like that would be fairly useless, so they must have a Canonical exception to break the normal snap constraints.

As for setup guides, I have found those written here: [https://www.howtoforge.com/tutorial/ubuntu-backup-deja-dup/](https://www.howtoforge.com/tutorial/ubuntu-backup-deja-dup/) to be reasonable.
But backup tools are useless until we test the restore - how else will we know it is working?  HInt: we don't.
The same website has a restore tutorial: [https://www.howtoforge.com/how-to-backup-and-restore-files-using-deja-dup-in-linux/](https://www.howtoforge.com/how-to-backup-and-restore-files-using-deja-dup-in-linux/)  Maybe this one is both - backup setup and restore?  IDK.

I'm not impressed with the example that shows only backing up a single directory under $HOME.  That isn't a terrible start for backups, but it is hardly all we need.  By getting just a few other places and some specific information, we can end up with a 1000x more useful set of back data.

---

### Post by HermanAB on 2022-07-25
It may be the default backup tool but I don’t know anybody that actually use it.  I tried it decades ago and it was kinda crummy - still seems to be kinda crummy.

---

### Post by ubontik22 on 2022-07-26
I've removed Déjà Dup and use *FreeFileSync. *If I find something more reliable I'll install.
Thank you

---

### Post by TheFu on 2022-07-27
> **ubontik22 said:**
> I've removed Déjà Dup and use *FreeFileSync. *If I find something more reliable I'll install.
Thank you

As long as the backup tool, meets most of these things, fantastic.
The Checklist

*    Stable / Works Every Time
*    Automatic
*    Different Storage Media
 *   Fast
  *  Efficient
 *   Secure
   * Versioned
  *  Offsite / Remote
 *   Restore Tested

There are lots of tools which do that.  A "copy" is not a backup.  Only 1 copy  (i.e. 1 version) is a failure.  On Unix-based systems, we've had fairly simple versioned backups possible for decades using tools that are already on the system. These don't have GUIs, because getting a GUI to run at 2am nightly is hard/impossible.  Automatic is one of the keys to excellent backups.

---

### Post by miguel001 on 2022-07-28
> **HermanAB said:**
> It may be the default backup tool but I don’t know anybody that actually use it.  I tried it decades ago and it was kinda crummy - still seems to be kinda crummy.

What?! Lol. I used it for years in Linux and its been stable and works great. Has its issues sure but all backup applications do.

> **ubontik22 said:**
> Hello everybody,

When I try to backup with Déjà Dup I get a message:

The gpg issue is familiar and may not be Deja dup itself. Unfortunately, I can't remember as its been some years since seeing gpg issue for anything.

I'm not sure if this happens if you only have gpg installed and not gpg2 or something along that line. That would be something people would miss as required packages are not always evident.

---

