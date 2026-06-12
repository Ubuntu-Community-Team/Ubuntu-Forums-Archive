---
title: "Files replaced by broken (link)"
date: 2017-07-04
forum: General Help
---

### Post by bignickel2 on 2017-07-04
Was doing KOTOR2 yesterday on my Ubuntu laptop with no issues.  Came back later, and found that it couldn't load any save games

Went into the save folder, full of little save game folders: every single file in those folders now says Link (broken), and is only 90 bytes in size.  When I do a properties on the file, it says type "Link (broken (inode/symlink).  They all point to the same folder that they're in , except with "/./" in the address somewhere:
/home/bignickel/.local/share/games/star-wars-kotor-2/./saves/000006 - Game5/Screen.tga

I created a test save file in the game, and they show up as regular files (not links) of whatever size theyre' supposed to be

I've searched my entire system (hidden files too), all that show up are these broken links, and my test file.

All my progress is gone unless I can find these things.  I may be somewhat of a noob to Linux, only using it for the last few years, but dang: I've never heard of Windows systemically going through and replacing whole bunches of files with broken shortcuts.  (And no: I didn't attach any usb or any device to the laptop yesterday; if that was the case, then i would think the shortcut would be pointing somewhere else instead of the exact location where the broken link is currently)
I've searched all over the internet; evidently no one has ever run into this issue before.

---

### Post by monkeybrain20122 on 2017-07-04
Those are symlinks (symbolic links) rather than actual files, they are broken because the files they point to have been removed or renamed somehow.  How did you install those games? Are they from wine? If yes they really live in .wine, you might have changed it somehow.

---

