---
title: "Sony Memory Stick Pro Duo 2 GB problem"
date: 2008-05-07
forum: General Help
---

### Post by Thanh-BKK on 2008-05-07
Hello.

I'm using Hardy 8.04 and my machine (Desktop, home built) has one of those internal many-in-one memory card reader devices.

It works fine, no problems - or so i thought.

Today for the first time i tried the Memory Stick from my digital camera, it is a genuine Sony 2 GB "Memory Stick Pro Duo". When i plugged it into the reader, it's activity light came on, "2 GB Media" showed up on the desktop and after quite some time (15 seconds?) a window opened, showing the lone folder on that stick.

I clicked that and got the lone folder inside the first one.

Clicked that, and in there are the pictures. Took a while for the icons to show up, and then it started building the preview thumbnails. All looked fine, altough surprisingly slow - well, all those pics are 2-2.5 MB in size. 

Once that process was completed, i "cut" one of the pics, opened a folder on HDD and "paste". 

That's where i got an error message - "unexpected error", which was indeed rather unexpected. 

I then tried to open that same picture, it started doing so but then just closed. Tried another one - no luck either.

I then tried to unmount the stick, it wouldn't let me - "An application prevents the media from being unmounted". 

So i did the "Ctrl-Alt-Backspace" to log out and back in, and there i got a barrage of errors (the stick still in the reader!) ranging from "Nautilus can not be used" to something "Bonono" or similar. No desktop wallpaper, no icons.

I shut down Linux, removed the stick and rebooted - it checked one of the HDD partitions (SDA6) and booted normally, everything seemed to work.

I put the memory stick back in, again it mounted, but now when i go to see the pictures only a few thumbnails show up and those look like corrupted, and NONE will open, i get an error something "invalid jpg200... something", i didn't write it down and now i'm at my office. However this time i could unmount the stick ok. Other pictures that are on the computer itself open fine, so no problem with the image viewer application.

Now plugging the same stick in my boyfriend's laptop (Windows) indicates no problem, all pictures are there and nothing is corrupted.

Oh, and my old Memory Stick, a 128 MB version, works fine, too, so the reader itself is working perfectly as well.

Is there a fix for this or do i just have to live with it? (Mind you, Windows refused to install when that memory card reader was plugged into the mainboard, so Linux is clearly ahead - however once Windows was installed and the reader plugged in, it worked fine and i didn't have to unmount as that device is actually "hot pluggable"). 

I hope this can be solved.... thanks in advance :)

Kind regards.....

Thanh

EDIT: Problem is solved - it wasn't with Ubuntu but HARDWARE. I swapped the reader device with another one and now it works fine. The old one didn't seem to support large storage cards - also MMC's, a 512 MB one was fine, a 2 GB one was NOT.

---

