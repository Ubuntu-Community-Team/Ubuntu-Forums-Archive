---
title: "Cannot empty trash"
date: 2008-04-24
forum: General Help
---

### Post by Wise Ferret on 2008-04-24
{FIXED}

Hello all,

I run hardy 32 bit on a reiser3 file system. My trash bin is full, but is not emptied when I right-click it and choose "Empty the deleted items folder". When I open it it shows two folders containing some text files (readme's). Following attempts to correct the situation have failed:
1. When trying to delete the folders manually from the waste basket I get the message "There was an error deleting <filename>."
2. When looking at the files from the waste basket, the right-click option "Delete from deleted items folder" is grayed out. Trying to view the text files yields the message "Could not open the file trash:///_<folder>/<subfolder>/<file>". When I try to delete one of the files with the delete key, I get the message "Error removing file: Permission denied".
3. When opening nautilus (with or without sudo), the folder /home/<user>/.Trash-<user>, appears to be completely empty. Deleting this folder does not help.
4. Running sudo reiserfsck from the liveCD in all possible correction modes did not change the situation.

Any clue on how to continue? How can I clear the trash once and for all?



{Found solution in another thread. I should have deleted manually everything from /home/username/.local/share/Trash/files}

---

### Post by themattjon on 2008-05-04
I could do this for my own account, but not for my girlfriend's, even using her password. What's up with that? How can I clear her Trash?

---

