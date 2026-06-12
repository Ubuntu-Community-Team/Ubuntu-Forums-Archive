---
title: "How to access the HDD Ubuntu is currently installed on."
date: 2008-04-28
forum: General Help
---

### Post by novaa on 2008-04-28
Hi.

I have four harddrives, labeled:
DISK 1, 2, 3 and 4.

I installed Wubi/Ubuntu on Disk 4. 

When I go to my computer or places in Ubuntu, all I can seem to access is only DISK 1, 2 and 3. But not 4.

This is a big problem, since all my music, movies, documents, series etc is on that disk....

Like...
Disk 4\Movies
Disk 4\Music
Disk 4\Ubuntu


How can I access my music in Ubuntu?

---

### Post by ago on 2008-04-28
/host

---

### Post by Nax10 on 2008-04-28
Thank you! I had the same question and now I know how to get to that drive.

Is there a way to show a hard disk icon on the desktop with that drive where Ubuntu is installed on?


And another similar question.

I have two internal drives 1, 2 and two USB external drives 3, 4.

When Ubuntu loads, it shows on the desktop shortcuts (links?) for the two external drives 3 and 4. That's great.

When I click on Places I see drive 1 and if I click it the Places menu, a shortcut for drive 1 appears on the desktop.

Is there a way to have that drive 1 icon stick on the desktop and the drive 2 icon (where my Ubuntu is installed on) stick on the desktop too? so I can get to all the drives with a single click from the desktop, and have all the shortcuts there very time Ubuntu starts?

Thank you for your help.

---

### Post by ago on 2008-04-28
You can always use symbolic links

ln -s /source/directory ~/Desktop/

replace /source/directory with the appropriate path

---

