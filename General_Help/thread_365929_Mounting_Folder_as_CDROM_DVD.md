---
title: "Mounting Folder as CDROM /DVD"
date: 2007-02-20
forum: General Help
---

### Post by arkangel on 2007-02-20
Hi pple :)

One question
Is possible to mount a folder and this acts as DVD or CDROM ?

---

### Post by capdog on 2007-02-20
Don't understand the question...? 

What you want is for a regular folder to be "seen" as a cdrom drive?

---

### Post by punx45 on 2007-02-20
i suppose you could create a disk image (.iso) of the directory.   im fuzzy on the details but read the man page for 'mkisofs'   i think you can then mount the image as a disk, however, the end result would basically be the same directory that you started with, but in a different location.

this does seem like a strange request. perhaps if we knew what you need this for we could be more help.

---

### Post by arkangel on 2007-02-21
> **capdog said:**
> Don't understand the question...? 

What you want is for a regular folder to be "seen" as a cdrom drive?

I have download a dvd   and I want to use the subtitles , it came out of my mind that mounting the folder as DVD or CDdrive will enable the XINE , or MPlayer to sincronize the subtitles with the movie 


I was thinking about the iso stuff  but maybe is possible  other way :)

---

### Post by capdog on 2007-02-21
I see... well I don't know if you can, but in my experience the DVD playing software has the option to play from hard disk, does that work? At least, this is the case with PowerDVD (windows). I'm relatively new to DVD on ubuntu.

---

### Post by M_the_C on 2007-02-21
Not sure if it would work (although I don't see why it shouldn't)  but you should do what punx45 said and make your folder an .iso then loop mount it.

[URL="http://www.granneman.com/techinfo/linux/burningcds/makeanisoimage.htm"]I found this tutorial on making an .iso from a folder.
[/URL]
[Here is how you mount the .iso.]("https://wiki.ubuntu.com/MountIso?highlight=%28iso%29%7C%28mount%29")

Once you have done this it should be just like mounting a DVD.

---

### Post by maher on 2007-02-21
use:
```

mount -o loop <your_image_file> <directory>

```

---

### Post by maher on 2007-02-21
sorry, my answer was for mounting an image into a directory
i guess i read you post backwards :)

---

### Post by punx45 on 2007-02-21
so you have a DVD rip that you are playing, and want subtitles?

it is possible that the DVD was ripped without them.

---

