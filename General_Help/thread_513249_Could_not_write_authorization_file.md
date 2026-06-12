---
title: "Could not write authorization file"
date: 2007-07-30
forum: General Help
---

### Post by slayer04 on 2007-07-30
"GDM could not write your authorization file . This
could mean that you are out of disk space or that your
home directory could not be opened for writing . In any
case it is not possible to login. Contact system administrator ."

I ok I am getting this error when I loggin and I think it is because the last thing I did when I was logged in was movie a bunch of video files to the trash can and I didn't empty it before logging out so I need to figure out how to empty the trash without logging in :biggrin:

---

### Post by strider1551 on 2007-07-30
> I think it is because the last thing I did when I was logged in was movie a bunch of video files to the trash can and I didn't empty it before logging out so I need to figure out how to empty the trash without logging in
No, that really shouldn't have anything to do with it.

First off, you can get yourself to a command prompt by pressing Ctrl+Alt+F1.  I recommend checking how much space is available by running the command "df".  You might also want to read through [this thread]("http://ubuntuforums.org/showthread.php?t=168447").

Edit:
On second thought, if those movies took up the last of your space, then that could do it.  use "rm -r ~/.Trash/*" to empty it from the command line

---

### Post by slayer04 on 2007-07-30
> **strider1551 said:**
> No, that really shouldn't have anything to do with it.
Edit:
On second thought, if those movies took up the last of your space, then that could do it.  use "rm -r ~/.Trash/*" to empty it from the command line

ok I did try this command but it keeps telling me the file directory does not exist also when I used "df" I got about 6file systems all of which checked out except "/dev/sdb2" which was 100% filled, I have no clue what it is

---

### Post by strider1551 on 2007-07-30
> ok I did try this command but it keeps telling me the file directory does not exist
This likely means that nothing is in your trash directory.  You can confirm with "ls ~/.Trash".  If .Trash itself doesn't exist, ls will inform you; if it is empty it won't print anything.


> when I used "df" I got about 6file systems all of which checked out except "/dev/sdb2" which was 100% filled, I have no clue what it is
I wouldn't worry about it.  So long as it isn't mounted as / or /home, it shouldn't be causing the problem at hand.

We now know one thing: there is enough diskspace to write the authorization file.  Have you tried the advice in that thread I mentioned?  It basically amounted to
```
rm ~/.ICEauthority
rm /tmp/gconf-(your user)
```

---

### Post by slayer04 on 2007-07-30
> **strider1551 said:**
> We now know one thing: there is enough diskspace to write the authorization file.  Have you tried the advice in that thread I mentioned?  It basically amounted to
```
rm ~/.ICEauthority
rm /tmp/gconf-(your user)
```

I actuality think it is because of their isn't enough space because I remember checking how much space was left and it was around 398 MB left and I moved a little under a GB of video from my flash drive to the trash also I have been using the commands you suggested and I get the same result with every command 
"No such file or directory"

Edit: also to let you know if this helps at all, I am running a dual boot system right now with windows on my c: drive and ubuntu on f: when I made the partitions I messed them up TWICE where on the drive Ubuntu has a little more than a GB of space so it wasn't all that hard to fill it up and that is why I think it is something with not entering the right command or because it is on the second partition  not primary it is set up like this [142GB ntfs] [1.2GB ext 3] and [4.5GB format unknown(can't remember)] the last partition if filled up

---

### Post by strider1551 on 2007-07-31
Well, you know your machine better than I do, so if you believe it is a matter of no space available, start deleting what you can.  I don't know your level of experience with the command line, so let me review a little.  "ls -la" will list all the contents of the directory you are in, including hidden files.  "rm <file>" will delete a file, bypassing the trash bin completely.  "rm -r <directory>" will delete a directory and everything under it.  "cd <directory>" will move you into that directory.

Use the "ls" command before and after every "rm" to comfirm for yourself that you deleted what you intended to.  When your finished, "df" will tell you how much space is now available.  When you have what you think is enough space, try logging in again.

---

### Post by slayer04 on 2007-07-31
I have little to no experience with the command line but what I do know is I have tried those commands repeatedly every end result is "no such file or directory" I have tried all the commands  you gave me but same result every time. that is why I am stumped, I used "df" again and nothing has changed it is all under 5% except /dev/sdb2 which is at 100% filled

Edit: wait could I just use my livecd to extend the patition that is filled up using gpated editor?? would that work?

---

