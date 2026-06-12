---
title: "Print problem: photo paper size 10*15cm (4*6inches) not fully printed"
date: 2007-05-26
forum: General Help
---

### Post by karhulitos on 2007-05-26
Hello,

I have HP Photosmart 8150 printer with photo paper 10*15cm (4*6inches) with tear off tab (16,5cm with tab). I've mainly taken photos with Sony Cybershot DSC-W12 with resolution of 1280*960 and 2592*1944.
This is Ubuntu 7.04 and photo software is F-Spot.

Now the problem is that when I print from F-Spot, the picture is not printed to the whole area of 10*15cm paper but it leaves 4mm vertical white borders to the left and right side of the picture. Top and bottom (landscape) do not have any borders at all.
Windows 2000 with HP's bundled photo manager software did print all the way if 'borderless size' was selected.

I gave this thought and wondered whether the picture's aspect ratio is such that it's not wide enough to cover the whole area of the paper. If this is true, then the HP's software must have done some automatic cropping or resizing so that aspect ratio is no longer original.

I found out that Eye of Gnome does scale the picture to the full area of the paper, so I can manage like this: F-Spot for managing & light editing -> send to EOG for printing. Unfortunately EOG does not seem to remember paper, orientation, print quality, etc setting, they need to be set everytime.

Please help if you know how to:
1. make F-Spot to print to whole area of paper (10*15cm)
2. make Eye of Gnome to remember printer and page properties by default

F-Spot would be the best as my wife won't remember long paths to do things, but in this case either one hepls!

---

### Post by karhulitos on 2007-05-26
It seems I was using wrong search words. [This ]("http://ubuntuforums.org/showthread.php?t=398506")one helped me to print borderless photos.

---

### Post by karhulitos on 2007-05-26
for my own future reference:

Borderless:
In CUPS ([http://localhost:631](http://localhost:631) or [http://127.0.0.1:631](http://127.0.0.1:631)), if I set my printer options as follows:
Page Size: Photo with tear off
Printout Mode: Photo (on photo paper)

F-Spot "shared mode":
1. move my ~/.gnome2/f-spot/photos.db to shared directory
2. chgrp users <shared_dir>/photos.db
3. chmod g+wr <shared_dir>/photos.db
4. ln -s <shared_dir>/photos.db photos.db when I'm logged in
5. ln -s <shared_dir>/photos.db photos.db when she's logged in

---

