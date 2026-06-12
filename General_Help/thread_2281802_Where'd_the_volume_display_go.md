---
title: "Where'd the volume display go?"
date: 2015-06-09
forum: General Help
---

### Post by Cleaver on 2015-06-09
Hi,

In Ubuntu 15.04, I used to have a display pop up and show a slider indicating what percentage the volume was at when I hit the volume buttons on my keyboard. This vanished a few days ago and I have no idea what caused that or how to get it back. What's most likely to be the solution? Thanks!

---

### Post by Innuend0 on 2015-06-10
The notifications are managed by notify-osd.

You can probably try to reinstall it.

>  sudo apt-get install --reinstall notify-osd

---

### Post by deadflowr on 2015-06-10
More likely to be a pulseaudio problem.
Seems like what I've seen in the past.
The solution I found was to delete or move the .pulse directory, then log out and then log back in.
The pulse directory should be in /home/user/.config/pulse << change user to your username.
(It's a hidden folder so in the Files program you need press ctrl + h to enable show hidden folders/files.)

For starter you might simply rename the folder, something like pulse.old.

From recollection the system will simply generate a new folder, clean and fresh.
But in case something bonks out, if you only rename the old one, you can still rename it back to the original name.
(As oppose to deleting it entirely)

Hope this helps.

---

### Post by Cleaver on 2015-06-15
Hi,

Tried both of those methods(in the latter case, I tried renaming the pulse folder to "pulse.old." No dice so far. I even rebooted to see if that would work.

I'm guessing deleting it entirely wouldn't make any difference. Any other ideas as to why it vanished so abruptly?

---

### Post by Cleaver on 2015-06-29
Any further tips here? None of the suggestions have gotten it back yet.

---

