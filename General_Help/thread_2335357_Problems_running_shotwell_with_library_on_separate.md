---
title: "Problems running shotwell with library on separate partition?"
date: 2016-08-27
forum: General Help
---

### Post by stuartclark007 on 2016-08-27
I am having problems getting Shotwell to run with the large library located on a separate drive.  I have downloaded and installed Shotwell, which has ended up in my root directory, a small flash drive. I have moved the library file to a much larger, ordinary mechanical, drive called "working".  Shotwell could not locate this the next time I ran it.  I thought it may be just a matter of establishing a Link from my boot drive to the working drive, but it still doesn't work.
Is this the way to do it, or is there some way of installing the application on the "working" drive, alongside it's library of photos?
Your advise and comments would be welome
Cheers

---

### Post by mook765 on 2016-08-28
I think a link should work.
The partition where your library is stored ("working") has to be mounted. You should mount this partition during boot using fstab.
The name of the link has to be exactly the same as the file you moved. When you created the link it might named "Link_to_filename", you would have to rename it to "filename".

---

