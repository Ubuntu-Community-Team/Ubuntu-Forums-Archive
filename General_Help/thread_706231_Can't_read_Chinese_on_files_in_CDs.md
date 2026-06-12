---
title: "Can't read Chinese on files in CDs"
date: 2008-02-24
forum: General Help
---

### Post by cisforcojo on 2008-02-24
I can read the Chinese name of the CD but can't read Chinese on anything contained in the CD. How can I set up Ubuntu to read Chinese in the CD files? When I try and run WINE, it can't process the Chinese characters and just goes faulty.

Any ideas? I've attached a photo of what I'm talking about.

EDIT: I should note that I have Chinese input working seamlessly on my system and can view Chinese files on my own system and desktop no problem.

---

### Post by cisforcojo on 2008-02-24
I can view the Chinese filenames now with: 
          ```
sudo mount -t iso9660 -o iocharset=utf8 /dev/cdrom /media/cdrom
          
```
    
          As you can see from the last attached photo, I cannot see anything inside the file and I still am having the same problem with WINE. Any ideas? This is really throwing me. I don't know what other params I could try for mounting. I've removed the serials from the file. :)

---

