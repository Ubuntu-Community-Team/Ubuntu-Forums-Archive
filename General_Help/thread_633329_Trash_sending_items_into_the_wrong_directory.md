---
title: "Trash sending items into the wrong directory"
date: 2007-12-06
forum: General Help
---

### Post by portach king on 2007-12-06
Hey Guys, 
After scouring the forum it seems that I have a problem that is quite unique.
Whenever I delete a file, it doesn't go into the .trash folder, instead it seems to head off to the /var/run directory. What's stranger is the fact that in spite of this is the trash still acts normally pretty much normally.  (ie. When I throw at item in there the trash icon transforms accordingly, and when I select empty trash it only deletes the files I did just send to trash). Meanwhile, .trash, remains empty constantly.
It's very strange behavior and irritating for a number of reasons such as, well because it's wrong, but also because if a change occurs in /var/run, the trash icon changes to look full. Which is confusing.
I uploaded a screenshot below, as you can see the contents of my "trash" and /var/run are pretty much identical.

So, any suggestions? 

Thank you in advance.

---

### Post by portach king on 2007-12-07
Hey, I don't to BUMP things but...
Anyone? Help?

---

### Post by viking777 on 2007-12-07
That is seriously weird if it is true.

You haven't got some sort of symbolic link between the two folders have you that is about the only thing I can think of. (it should have an arrow on the icon donating a link).

BTW looking at what you have in your trash folder I wouldn't be in too much of a hurry to empty it if I were you, if you delete hal, dbus, cups, network and a few others like that you aren't going to have much of a system left!!

---

### Post by portach king on 2007-12-07
Thanks for replying.
Well when I empty the trash can, it doesn't touch any important files, it just deletes whatever sent there.
There's is no link either btw. No icon and nothing in the preferences that indicate so.
Besides that folder is very heavily gaurded... I don't understand how trash is achieving the permission to put files in there in the first place.

---

### Post by viking777 on 2007-12-07
Sorry my friend but I really don't know the answer to that one:(

---

### Post by portach king on 2007-12-07
Ah well, thanks for trying. 

Maybe someone else who see's this will.

: )

---

### Post by imbjr on 2007-12-10
I'm looking into this right now.

My trash: URI is also pointing at /var/run (and /home/<me>/.Trash). 

When I looked in /home/<me>/.Trash, only the files I knew were deleted were listed.

---

### Post by imbjr on 2007-12-10
[https://bugs.launchpad.net/ubuntu/+bug/120884](https://bugs.launchpad.net/ubuntu/+bug/120884)

To quote the bit that helped:

> 
I encounter the same problem.
Instead of deleting the file .trash_entry_cache, I edit it:

Original file:
/dev/shm -
/lib/modules/2.6.20-16-generic/volatile -
/proc/bus/usb -
/var/lock -
/var/run /var/run

Edited to:
/dev/shm -
/lib/modules/2.6.20-16-generic/volatile -
/proc/bus/usb -
/var/lock -
/var/run -

Not sure exactly what the changes did, but it worked. After logout/login, the trash is back to normal.


I had something like:
/dev /var/run
in there!!!

Well that was a night wasted. This has been one of those (thankfully) rare occasions where I could punch linux/Ubuntu in the head.

---

### Post by portach king on 2007-12-12
Wow, thank you so much. 
Kinda glad I wasn't alone.

*proceeding to fix*

By the way, this was reported in July? Hmm..

---

