---
title: "How do I Sync a Local Folder to a Local Folder?"
date: 2018-05-20
forum: General Help
---

### Post by UbuntuWho on 2018-05-20
This is a rather complicated matter, so I'm going to explain what I mean...

I have a set of files in a folder that I want to sync with another folder. Now, this is not a folder on a server; it is on the same computer. Also, both folders are owned by the same user. I realize that I can do cut-and-paste, but consistently doing this gets monotonous and time consuming. What I want is a program that can do this for me. This way, I can save any documents in the primary folder (the one my program uses) to the secondary folder (the backup synced with the primary), and if somehow I lose my progress or want to revert to earlier documents, I simply reverse the direction of the sync and overwrite the files in the primary folder with the ones in backup. All it takes is a click of a button, and presto! The copy is done.

So, what are my options? I'm looking for something simple, yet configurable. I prefer a GUI program; running a bash script would be *too* simple, and not really convenient. I also want this program for Linux Mint, so it can't be just an Ubuntu-only program. It *can*, however, be Ubuntu-based, as the Linux Mint computer is not using LMDE (Debian-based).

---

### Post by pvanryn on 2018-05-20
I use Double Commander for this. Open the directories you want to sync,and then hit the "synchronize" button. Pretty simple.

---

### Post by UbuntuWho on 2018-05-21
> **pvanryn said:**
> I use Double Commander for this. Open the directories you want to sync,and then hit the "synchronize" button. Pretty simple.

Very good, however I wasn't expecting an alternate file manager. Perhaps something simpler?

---

### Post by btindie on 2018-05-21
Easiest option is just to create an rsync script and place it in your ~/bin directory.

Then when you want to sync the directories just type the command into a terminal.
```

#!/bin/bash

# Don't include trailing slashes
SRC_DIR=~/Documents/Project
DST_DIR=~/Backup/Project

# add --dry-run option to the below to see what it will copy without any changes being made
rsync -avh "$SRC_DIR/" "$DST_DIR"

```

save the above to ~/bin/prog-sync, update SRC/DST variables to point to the correct location and run "chmod +x ~/bin/prog-sync" to make it eXecutable.

---

### Post by Qassis on 2018-05-21
Pvanryn, this solution may not meet the requester's need but it sure was a good suggestion that meets mine. 
Thanks.
qassis

---

### Post by UbuntuWho on 2018-05-21
> **btindie said:**
> Easiest option is just to create an rsync script and place it in your ~/bin directory.

Then when you want to sync the directories just type the command into a terminal.
```

#!/bin/bash

# Don't include trailing slashes
SRC_DIR=~/Documents/Project
DST_DIR=~/Backup/Project

# add --dry-run option to the below to see what it will copy without any changes being made
rsync -avh "$SRC_DIR/" "$DST_DIR"

```

save the above to ~/bin/prog-sync, update SRC/DST variables to point to the correct location and run "chmod +x ~/bin/prog-sync" to make it eXecutable.

Well, it's better than having to use a file manager, however I was looking more for a GUI option. Sorry, I'm not trying to make this difficult; I just don't think that this is what I'm looking for.

---

### Post by The Cog on 2018-05-21
You could try grsync.
Or make a desktop launcher icon for the above script. 
It's difficult to know exactly what you are looking for.

---

### Post by UbuntuWho on 2018-05-21
> **The Cog said:**
> You could try grsync.
Or make a desktop launcher icon for the above script. 
It's difficult to know exactly what you are looking for.

PERFECT! \\:D/ Grsync is just what I was looking for! Thanks, Cog! :biggrin:

---

