---
title: "Recover any windows files?"
date: 2020-06-01
forum: General Help
---

### Post by jm04 on 2020-06-01
Hello, I thought I backed up this text file I needed when switching from Win10 to Ubuntu, but seems I havent.
Is there any way to recover it?
I have overwritten windows

---

### Post by Autodave on 2020-06-01
None that I am aware of.  Sorry.

---

### Post by TheFu on 2020-06-01
Doubtful.  Is this file worth 20 hrs of recovery attempts?  The chance that the file can possibly be recovered depends completely on chance - that no new data was written to the blocks where the file was stored.  Are you prepared to go through 500,000 randomly named recovered files to find this 1 file?  **photorec** and a new HDD where you can restore all those random files will be needed. photorec is part of the testdisk program.

BTW, best not to run Ubuntu from that disk. Do all this work while running from a flash drive.  Restore the files to a different disk, not the same one from which you need to recover data.  If the data to be recovered is on a data-only disk, not a running OS, then it is fine to use that OS install.

Also, the file may not be complete. Parts of the different blocks used by the file could be available, but others may have been overwritten. You'd need to manually determine the order of those blocks if the parent-child relationship between them has been broke.

If you zero out storage blocks from time to time, data recovery like this in the future could be much faster.  Just be certain you don't zero out unused storage if you need to restore any data. There might be reasons NOT to zero blocks on SSDs too. IDK. I wouldn't without doing specific research about that to ensure it doesn't negatively impact the live of the storage.

Good luck.  Depending on the total size of the disk, it could take a very long time and the company cannot be used for anything else while this is happening.

---

### Post by jm04 on 2020-06-01
Thanks for the reply!
It was a recovery code for Brave Browser where I held like $50 worth of BAT. Not a big deal I guess and probably not worth the hassle.

---

### Post by TheFu on 2020-06-01
> **jm04 said:**
> Thanks for the reply!
It was a recovery code for Brave Browser where I held like $50 worth of BAT. Not a big deal I guess and probably not worth the hassle.

Stuff like that gets placed into my password manager.

---

### Post by jm04 on 2020-06-01
That wouldnt be a bad idea I suppose, you live and you learn I guess haha

---

