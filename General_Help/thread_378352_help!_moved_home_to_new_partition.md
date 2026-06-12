---
title: "help! moved home to new partition"
date: 2007-03-07
forum: General Help
---

### Post by olavjunior on 2007-03-07
I used the  guide from pigpond.net on how to move home to a new partition. 

Restarted and everything seemed fine. But, suddently compiz wasn't running on startup, along with cairo-dock, my desktop, my gnome-docks ect ect. Everything was gone, just like a clean install. Same story for all aps, they were running as if it was the first time!

What's the reason for this? All my ./folders are in my home-dir, and the backed up home is the exact same size as the new one. 

:S

EDIT: 
I was smart enough to take a backup with sbackupd. I started the restore-prosess, but some warning popped up (it was blanck, and everything hung) After a while I tried to close the window, but nothing happend. So I pressed ctrl alt backspace, and logged into xwindows again. I then tried to run sbackupd through terminal to see if it acctually was running, and it was! But I have no clue on how far it has gotten in the restore prosess. 

I've configured my main things over again. Compiz is running fine, and now everything is back to normal :) The only thing I miss now is the evelution settings. Anyone know where they are stored?

SOLVED: Used the commands
$ gconftool-2 --shutdown
$evolution --force-shutdown

to get Evolution up and running again. After that everything was back to normal :) 

So if anyone else is wondering, I'll leave this standing as solved :)

---

### Post by Darko Beta on 2007-03-07
Olav,

I have run into the same problem in the last day, and I came across your post when I was searching for some help.  The same thing happened: firefox and everything was wiped clean as if it was new.  I don't really mind setting those things up again except for Amarok, which contains a ton of ratings and database info on my music!  It sounds like that is how you felt about Evolution--so would $amarok --force-shutdown restore these things?

---

### Post by floke on 2007-03-07
It depends on the way in which you copied your data over to the new partition. If you used a graphical app. such as nautilus, and if you did this with the 'sudo' command, then this explains it - since using sudo to open a graphical app. will open it with the root settings (and hence will not have transfered over your own settings). To transfer your own settings this way you need to use the 'gksu' command - since this will open a graphical app. with your settings.

Hope this makes sense (it happened to me once too!)

---

