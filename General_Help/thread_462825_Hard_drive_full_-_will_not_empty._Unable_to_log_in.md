---
title: "Hard drive full - will not empty. Unable to log in."
date: 2007-06-03
forum: General Help
---

### Post by alchemy101 on 2007-06-03
Really cheesed off on this one!
I ran the program to clear the empty space a few times on the hard drive (scratch?). Anyway, i deleted the file it created, at the end, but noticed that my filesystem still read '0 bytes free'.
I went to the recycler, but it was empty. Checked the temp folder, emptied it, hard drive full.

At this stage, i got a few emails, but they wouldn't download, on account of the drive being full.

I thought a restart might fix it...

Now i can't log in, as it can't make my tmp file. 

I simply can't believe this - how could the recycler not actually delete files, and if so, where have they gone now? Doesn't ubuntu delete them on exit / restart? 

My windows dual boot is now inoperable (due to ubuntu removing some stuff from it when making a drive readable), and i think i may be able to get into terminal. Naturally, all my stuff is locked away. 

Is there any way to actually make it DELETE the files i ASKED it to delete? Is there any way to log back in after the harddrive refused to show free space? I've got to get back onto this computer.

---

### Post by hellmet on 2007-06-03
Did you try Ctrl-Alt-F1 at the Login? I'm not sure if the terminal would open during such a situation. I'm not sure why your files weren't deleted. Maybe they were locked(??). 

The last time I had such a problem, I booted the LiveCd, mounted the partition, and deleted a few files and I got in . :) .. Don't get frustrated. :) Stay cool!!

---

### Post by alchemy101 on 2007-06-03
Thankyou - i will go and try that. How can one actually delete the files to make space? I shift-deleted my hard temp folder, but it didn't clear any space.

Where can i find out where that file went, and delete it? I've got to find it first.
Thanks!
(attempting to stay calm :)

---

### Post by Nehvrook on 2007-06-03
Maybe the stuff you deleted is just in a hidden file. Like ".trash". Use the liveCD and see if you can find something like that

---

### Post by alchemy101 on 2007-06-03
Well the live cd really does make my computer locked up, so i'll need to do this through the terminal.

I deleted this massive file through nautilus, so the file should be located in /root/.trash  (which is a hidden folder). I guess.

How can i view hidden folders in terminal, and how do i properly delete them?


EDIT:
I have managed to find my way to the / level (bin, etc, mnt, sbin ....) and i'm looking for this file.
The scratch directory, in which i used nautilus to delete the file, is empty. I've tried ls -h in it, but no hidden files (i'm guessing the syntax here).

What CAN i delete to make some space? How can i find this file?

Really need some help on this - i'm stuck with a lot of colourful text, but no files :(


Using ls -la in the scratch directory, it says 
drwxr-xr-x 2 root root (lots of numbers)
drwxr -xr-x 22 root root (lots of numbers)

Are these my files? Should i 
sudo rm drwxr-xr-x

---

### Post by alchemy101 on 2007-06-03
Success!  sudo rm -r .Trash in the root folder has done it correctly. Talk about hard to do.
At least i won't make that mistake again.
Thanks for the help

---

### Post by hellmet on 2007-06-03
Thats great .. happy ubuntuing.

---

