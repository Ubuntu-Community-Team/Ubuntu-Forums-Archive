---
title: "File roller error on extracting large Rar seems to cause /tmp problem"
date: 2014-07-29
forum: General Help
---

### Post by Retfar on 2014-07-29
So here are the particulars:
- I have a large rar archive (10.1gb)
- Extracting ~500mb or less at a time gives no error
- Extracting more gives a unspecified error
- Terminal lists me as the user, but I no longer have write access to any files (I can still read any)
- Logging out gives error 'failed to start x server'
- Restarting gives boot error about failing to mount a drive (I only have 1), which upon repair the next message is about /tmp failing to load 
- Upon completion of reboot all is back to normal

Other interesting points:
- I have extracted large-ish (~5gb) rars before without any problems, so it is possible there's something wrong with the specific archive, but if so, why would it create such an issue?
- After the error has occurred it seems the loaded permissions file has gone, since when trying to use a command that requires sudo terminal gives me something about being unable to verify permission
- I run Mint 16 (Cinnamon), ie. Ubuntu 13.10
- file roller version 3.6.3 (I understand it's only a graphical front end, but I'm assuming it comes with the corresponding libarchive version)
- I have (relatively) plenty of free space (160/500gb) and it's formatted as Ext4

What I'm hoping to learn:
- Am I doing something/configured something terribly wrong?
- Is there some larger picture constraint I missed? (like a 10gb archive limit)

That's the general overview of what happened (twice). The errors I gave were general summaries as I didn't write them down and i didn't particularly want to go through the process a third time (it certainly doesn't seem good for my beloved lappy). The files are not particularly important to me and I will be fine without them, but I didn't find a similar issue googaling so if nothing else if someone does have something they really care about extracting and this happens, they'll know how to make it work.

---

