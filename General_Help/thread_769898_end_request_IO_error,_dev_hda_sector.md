---
title: "end_request: I/O error, dev hda sector"
date: 2008-04-26
forum: General Help
---

### Post by 828688 on 2008-04-26
I've been having hard drive problems since a long time now (previous messages posted by me) and I could cope with it by using fsck and forcefsck and booting with the ubuntu's recovery mode version.

the hard drive started ticking again, so I turned it off for a while and I tried turning the computer back on. It worked for a little while sometimes, and sometimes it would last for several hours without any single problem.
After turning it off I tried using the recovery mode again and after using all the text displayed while booting it, it ran part of fsck and then it started displaying all over the screen, like flooding the screen with things like:

(numbers.numbers) end_request: I/O error, dev hda sector (numbers)

The numbers on the left were changing a lot, as if they were counting, the numbers on the right were the same. It has been doing this for a long while now. (it seems to me like it's scanning every single thing, but I don't have any idea)

I tried inserting the live cd (which is right now inside the computer) but I didn't place any command to run the live cd. as far as I have seen, the led on the cd player isn't even on and personally I don't htink it runs itself automatically...

I would like to know if I need to leave the computer on until it finishes or just turn it off right now, again wait for it to cool down and try again booting it with recovery mode along with fsck.

thanks in advance.

---

### Post by uscpsycho on 2008-12-05
> **828688 said:**
> I've been having hard drive problems since a long time now (previous messages posted by me) and I could cope with it by using fsck and forcefsck and booting with the ubuntu's recovery mode version.

the hard drive started ticking again, so I turned it off for a while and I tried turning the computer back on. It worked for a little while sometimes, and sometimes it would last for several hours without any single problem.
After turning it off I tried using the recovery mode again and after using all the text displayed while booting it, it ran part of fsck and then it started displaying all over the screen, like flooding the screen with things like:

(numbers.numbers) end_request: I/O error, dev hda sector (numbers)

The numbers on the left were changing a lot, as if they were counting, the numbers on the right were the same. It has been doing this for a long while now. (it seems to me like it's scanning every single thing, but I don't have any idea)

I tried inserting the live cd (which is right now inside the computer) but I didn't place any command to run the live cd. as far as I have seen, the led on the cd player isn't even on and personally I don't htink it runs itself automatically...

I would like to know if I need to leave the computer on until it finishes or just turn it off right now, again wait for it to cool down and try again booting it with recovery mode along with fsck.

thanks in advance.
This happened to me while running ddrecover. I am trying to clone my failing drive with ddrecover and after about a day of what seemed to be a successful clone my screen has been flodded with this error for nearly 24 hours now. Except for me the sector numbers on the right are incrementing by one on every line.

While this is happening there is no action on my target drive (write light never comes on) so nothing is being transfered.

I was optimistic about the success of the data recovery until this happened. Can anyone shed some light on this?

---

### Post by ByteJuggler on 2008-12-05
> **uscpsycho said:**
> This happened to me while running ddrecover. I am trying to clone my failing drive with ddrecover and after about a day of what seemed to be a successful clone my screen has been flodded with this error for nearly 24 hours now. Except for me the sector numbers on the right are incrementing by one on every line.

While this is happening there is no action on my target drive (write light never comes on) so nothing is being transfered.

I was optimistic about the success of the data recovery until this happened. Can anyone shed some light on this?

Well, remember: The idea behind ddrescue is to copy first all the  undamaged areas of the disk, then go back and try to recover the bad areas. On the former task it will spend relatively little time, allowing you to quickly have a mostly complete image (excepting for the bad holes), and then have ddrescue try for some extended period of time to recover data from the damaged sectors.  This process can take a very long time depending on what's actually happened inside your hard disk.  A head crash on a certain platter for example will mean that you'll have zillions of "bad" sectors which will probably be relatively unrecoverable.  If you however tell ddrescue to try hard, it will spend long trying to copy those sectors.  Have you read the ddrescue man/info pages?  Can you post the command line you're using to recover your disk please?  Try opening a terminal and entering "info ddrescue".  (You might have to do "info info" as well ;)  )  You can IIRC also access the info pages using the Gnome Desktop help system. (I'll have to check how exactly, but probably by pressing F1 and searching, I'd imagine.)

---

