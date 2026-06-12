---
title: "Problems with folders imported from windows xp"
date: 2008-04-06
forum: General Help
---

### Post by jonask on 2008-04-06
I have transfered some folders with images from my old windows XP computer to my new one with ubuntu 7.10
When I look in the folders using the folder browser or using the terminal they are all empty. However digicam and picasa2 are both able to find the images. 

When I use the wine file utility it is also possible to see the files in my folders.

I have enabled reading and writing for all the folders  (chmod a+rwX -R *) but the folder browser still says that they are empty. 


All suggestions would be really appreciated. I guess it is probably something obvious.

cheers

Jonas

---

### Post by 67GTA on 2008-04-06
What extension do  they have?

---

### Post by Gen2ly on 2008-04-06
If you know the name of any of the photos you can use:

```
find / -name NAMEOFPHOTO.JPG
```

This will search the whole hard drive so it may take awhile, also remember that Linux is case sensative.

---

### Post by jonask on 2008-04-06
[SOLVED] :) Thank you so much for the help. It worked with FIND I copied my PICTURE folder over once, but it only copied the subfolders because the pictures were hidden. After changing this I must have copied my pictures over again into my old PICTURE folder. I have more then 1000 folders so I didnt see this.

---

