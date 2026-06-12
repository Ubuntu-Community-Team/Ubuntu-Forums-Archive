---
title: "Mounting ext3 partition as $HOME"
date: 2005-04-21
forum: General Help
---

### Post by #Vizc@ch@ on 2005-04-21
Hi, i'm trying to add more space to my Ubuntu, so i tried with Partition Magic and succesfully shrinked the windows partition, but when i wanted to resize (add more space) to my Hoary partition mounted on / I got an error from Partition Magic.

So I decided that i would create another ext3 partition so that i could mount it whenever i wanted and use it as storage.
But now, I thought that why don't I mount this new partition (hda4) in my home directory, and have it mounted automatically at boot up. 

My question is: 

How can i safely do this? I don't want any of the files in my $HOME directory erased.
Should I just write fstab and mount hda4 in /home, or is this dangerours, or are my files going to be erased?

Hope I didn't make to many spelling mistakes.
Thanks for the help

---

### Post by heimo on 2005-04-21
I assume the old /home is not on its own partition and that the new partition is already initialized (mkfs.ext3 for example). and that it's normal desktop system. (Silly disclaimers... from anyone who works with servers.)
 
I would rename (mv) /home to /home_old, create new fstab line for new partition (mountpoint /home), create empty /home directory, mount new partition (/home), copy everything from /home_old to /home using proper flags to preserve user:group permissions (probably cp -a), check that everything is ok and remove stuff in /home_old when disks start to get too full (not immedieately).

---

### Post by #Vizc@ch@ on 2005-04-21
Ok, thank you very much  :grin: 
Just one question: Would the command cp -a also move to the new /home the hidden files? and the configuration files? Cause i'm worry i'm gonna mess up some config. stuff  :-?

---

### Post by heimo on 2005-04-22
That's a real concern. Remember to do it as root. You may have some files that are owned by root in your home partition - or owned by other users. Then use something like
 ```
cp -a from/. to
``` 
where from is the directory you're copying and to is existing new directory.

Do **NOT** use * or *.* - you will not get all files. Use dot. Other approach would be to tar everything and pipe it to extracting tar... You could take advantage of your CPU power to make transfer faster, but that's another story. :) (EDIT: Hmm.. I'm not sure if that'd make any difference in this case)

Oh, and did I say: Backup all your valuable information before any major changes.

---

### Post by #Vizc@ch@ on 2005-04-22
Ok, I think i'll give it a try :grin:
Thanks heimo!

---

