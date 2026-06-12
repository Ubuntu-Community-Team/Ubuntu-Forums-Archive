---
title: "ntfs-3g alert before delete"
date: 2007-09-11
forum: General Help
---

### Post by s-lime on 2007-09-11
I successfully installed **ntfs-3g**, and I noticed that file deletes automatically if i hit DELETE key, without promting (like in windows) if I really want to delete a file/folder...

Because files from NTFS doesn't go to trash this is a serious problem. 

Please help.

---

### Post by merlinus on 2007-09-11
If you need a warning and/or a trashbin, then format the drive as ext3 and install fs-driver to write to it from windows.

OTOH, a simple double-check before pressing Del might work....

---

### Post by s-lime on 2007-09-11
Thanks for answer.

Isn't the removing DELETE key from keyboard by force best idea?

Formating is simply not an option and destroying my keyboard neither, what do you think? Any other ideas?

---

### Post by merlinus on 2007-09-11
LOL...

I was not suggesting that you destroy your keyboard....

I do not think you will get an ntfs trashbin or deletion alert from ubuntu.

---

### Post by s-lime on 2007-09-11
:D

thanks... I will be careful with delete key. :KS

---

### Post by thinsoldier on 2007-10-24
My cat knocked a pen off the top shelf of my desk.
Landed right on the Delete key.

9 gigs of training videos GONE.
18 gigs of Anime GONE.
Grandmother's 90th birthday party photos G O N E.
7 gigs of stock photography, artwork, and .psd's GONE.
20+ gigs of .mp3s GONE

...... %$&@.......
Luckily the [burnt_already] folder was highlighted and not the _toBurn folder.
But still. That **** ain't cool!
How the %$&@ do I make my ntfs drives read only again?

---

### Post by noynac on 2007-10-24
> **thinsoldier said:**
> My cat knocked a pen off the top shelf of my desk.
Landed right on the Delete key.

9 gigs of training videos GONE.
18 gigs of Anime GONE.
Grandmother's 90th birthday party photos G O N E.
7 gigs of stock photography, artwork, and .psd's GONE.
20+ gigs of .mp3s GONE...

How the %$&@ do I make my ntfs drives read only again?
On my computer with Gutsy, deleted directories and files on NTFS-formatted drives are placed in a hidden directory with the name .trash-<username>.

BTW, Gutsy has the built-in ability to access, modify, and delete files and folders on NTFS-formatted drives. There would appear to be no reason to install NTFS-3G. Perhaps the OP was not running Gutsy at the time of his post.

---

### Post by thinsoldier on 2007-10-25
You have no idea how happy I am right now.

For anyone else finding this:
Look for the .trashes-usernamehere folder in the root of the drive and not the folder that contained the stuff you deleted.

---

### Post by usererror on 2008-05-27
if I go to / there is no .trashes folder, where is it in 8.04?

---

