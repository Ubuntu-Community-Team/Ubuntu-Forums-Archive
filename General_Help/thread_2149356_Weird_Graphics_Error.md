---
title: "Weird Graphics Error"
date: 2013-05-28
forum: General Help
---

### Post by colek42 on 2013-05-28
Graphics Card:  ATI 6570
Screenshot:  See Attached File


I was having this issue after an upgrade to 13.04.  After some messing around I got the screen to go back to normal but had random crashes and lost my desktop bar (unity).  I decided to do a complete fresh reinstall on a formated HD, I downloaded 12.04.2 LTS and am having the same issue.

Any Ideas?  I need to get the server running before the wife gets home.

---

### Post by dino99 on 2013-05-28
what you are seeing is named "plymouth" and seems hanging while booting. You can get the verbose mode, and see what is happening, by removing "quiet splash" from the the line you boot on (inside the grub menu: ctrl+h to unhide it on a single OS system installation) and then continue to boot by validating the change

---

### Post by colek42 on 2013-05-28
It is hanging at different spots.  it is tough to read to output because the screen is split.  even when I ctrl-alt-f1 the screen is split.  Something in the most recent update does not want to work with my graphics card.  This is very frustrating as this server controls my security cameras, NAS, Media servers, TV, etc.  Going to give mint a try and see what happens.

---

### Post by colek42 on 2013-05-28
Linux Mint 14.1 mate works perfectly

---

