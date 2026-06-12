---
title: "Restoring deja-dup backup on xubuntu doesn't work - GPGError"
date: 2015-01-07
forum: General Help
---

### Post by eyal-ez on 2015-01-07
So I come here after a considerable amount of research, the facts I managed to collect are so:
When I made those backups (xubuntu 14.04, same as the fresh install I'm trying to restore on), I had a few errors regarding several folder which couldn't be backed up on because they were owned by root (.dbus, .gnupg, .gvfs and maybe another I can't remember).

The error I receive while trying to recover is as follows:
gpg: fatal: zlib inflate problem: invalid code lengths set

I tried using duplicity, tried decrypting it with GPG - getting that same error on all 3. From my searches online I came to the conclusion that because my .gnupg folder wasn't backed up, my gpg public key is lost and there is no way to restore that backup (unless I do it on the same machine it was made on) without it. Unfortunately that installation is lost and I cannot recover it.

Is this correct? Is there something I can do to restore this backup?
And on a different note, who should be the owner of those folder I mentioned above and if root is the answer - how do I include them in the backup (should I run deja-dup with sudo)?

Feeling a bit lost and frustrated, I'll appreciate any help.
Thanks!

---

### Post by TheFu on 2015-01-07
Don't know about dejadup - don't use it.  If there is a gpg error, then you'll need to gpg keys used to encrypt it do decrypt it. That's just the way gpg works. If you don't have those, unless you are the NSA and really, erally, really, really, want it, there isn't any hope.  For you and me - our backups are gone. Get over it.  

Learn from this.
* always verify you nkow how to restore and 
* always TEST the restore before you need it on a different computer, preferably in a different location only with the backup data.  This way you'll discover whether everything you need to restore is available.  

In general, gpg keys need to be stored and guarded like they were all the water/oxygen on earth. Having them included inside the encrypted backups won't help - you need these keys to access the backup data.

So - moving on ... to other questions.
* No, you should NEVER run any GUI program with sudo. There are many reasons why this is so.
* You may want to perform backups as root - it depends, but if you want a complete system backup, it is mandatory to use a root-equiv account.
* You may not want to perform backups as root - if the things being backed up are just owned by 1 userid - like the /home/userid ... where personal data is.

There are tutors for file and directory permissions over at help.Ubuntu.com which might help clarify.

---

### Post by eyal-ez on 2015-01-07
Thanks for the info:)

I managed to salvage most of my files by manually decrypting them (all files accepted my password, the problem was with the sigtar files..).
I acquired some knowledge and wrote a python script to help speed things up. More info here for future reference:
[https://github.com/eyalzek/multivol_snapshot_fix](https://github.com/eyalzek/multivol_snapshot_fix)

---

