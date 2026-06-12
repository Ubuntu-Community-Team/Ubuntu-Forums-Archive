---
title: "How to store thumbnail preview on same partition as original image?"
date: 2007-10-11
forum: General Help
---

### Post by alvevind on 2007-10-11
It seems that all thumbnail previews for images and movies are always stored in the folder /home/myusername/.thumbnails/

I would rather have thumbnails stored on the partition where the original files are located.  E.g. if my large photo archive is located on an 500GB external harddisk, the thumbnails should also be  stored physically on that harddisk, not on my already full 5GB /home laptop partition. 

Was thinking in turns of a ".thumbnails/" folder in each of the original folders, or maybe a database file on the root folder of the external partition. Doesn't matter how it's done as long as the thumbnails follow the original files partition and don't clutter up my /home partition.

Suggestions?

---

### Post by dcstar on 2007-10-11
> **alvevind said:**
> It seems that all thumbnail previews for images and movies are always stored in the folder /home/myusername/.thumbnails/

I would rather have thumbnails stored on the partition where the original files are located.  E.g. if my large photo archive is located on an 500GB external harddisk, the thumbnails should also be  stored physically on that harddisk, not on my already full 5GB /home laptop partition. 

Was thinking in turns of a ".thumbnails/" folder in each of the original folders, or maybe a database file on the root folder of the external partition. Doesn't matter how it's done as long as the thumbnails follow the original files partition and don't clutter up my /home partition.

Suggestions?

Make your .thumbnails a link to a location where you have space - but they will still all be stored in one location.

---

### Post by alvevind on 2007-10-14
> **dcstar said:**
> Make your .thumbnails a link to a location where you have space - but they will still all be stored in one location.

Thank you. But it does not solve this issue. If I have two external disks, A and B, I want the thumbnails for A to be stored on disk A, and thumbnails for B stored on disk B. I do not wish to always connect both external disks because /home/username/.thumbnails is set to point to disk B.

Anyone have an idea of a solution? :confused:

---

### Post by rax_m on 2007-11-04
I actually have the same issue... 
did you find a solution yet ?

---

