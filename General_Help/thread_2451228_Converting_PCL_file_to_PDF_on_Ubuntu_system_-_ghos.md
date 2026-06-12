---
title: "Converting PCL file to PDF on Ubuntu system - ghostpcl not working - alternatives?"
date: 2020-09-29
forum: General Help
---

### Post by wb0gaz on 2020-09-29
I've got an old electronic instrument that screen prints its display by generating a PCL file. My goal is to convert the PCL file to PDF (or some intermediate step that will get me to PDF.) These are small files and the instrument is quite old (vintage late 1980s.) I need to do this processing in Ubuntu environment (not windows.)

ghostpcl (based on ghostscript) is available for Linux (and Windows) but the Linux version (9.53.2) terminates with a couple of PCL format errors (the windows version of the same software works fine on the same small PCL file, but I cannot do this processing in a Windows environment.) After some searching, I'm not sure where I'd pose the compatibility issue with Artifex Software (the outfit that seems to be responsible for GhostPCL).

Where could I find a utility that works in Ubuntu environment that renders PCL into some format that will get me to PDF, with the caveat that ghostpcl does not appear to work as noted above? Are there alternatives? Am I missing something basic about the world of PCL?

Thanks much for any advice or pointers as to where I could pose this question!

Dave

---

### Post by HermanAB on 2020-09-29
Did you try *convert*?

[https://linux.die.net/man/1/convert](https://linux.die.net/man/1/convert)
[https://imagemagick.org/script/convert.php](https://imagemagick.org/script/convert.php)

---

### Post by GhX6GZMB on 2020-09-29
> **HermanAB said:**
> Did you try *convert*?

[https://linux.die.net/man/1/convert](https://linux.die.net/man/1/convert)
[https://imagemagick.org/script/convert.php](https://imagemagick.org/script/convert.php)


PCL is not a graphics format, it's the command and data stream to the printer.
The way forward would be a printer emulator. After that, the capture can be converted to anything. I've found some, but they're not free. 
Whether there are free projects underway: no idea.

---

### Post by HermanAB on 2020-09-30
Convert should be able to do it and it is as easy as:
*$ convert file.pcl file.pdf*

If you read the manual then you can adjust the quality.

---

