---
title: "Timezone difference killing FSCK"
date: 2007-03-20
forum: General Help
---

### Post by Aphoxema on 2007-03-20
I'm having a simple problem that I can't quite figure out the solution to...

I'm migrating from WinXP to (X)ubuntu, and in WinXP I'm using 'EXT2 Installable Filesystem' to access my EXT3 filesystems. Everytime I mount them (and eventually unmount them) with IFS, the date is set to what Windows has it as.

When I'd go into Xubuntu (until I set all the passno's to 0), FSCK would exclaim all the filesystems I had mounted were last accessed in the future and run a full check on them.

I have my BIOS clock set to local time, and I want Xubuntu and WinXP both to work off only that, because I think timezones are getting into the mess somewhere and resetting things.

---

