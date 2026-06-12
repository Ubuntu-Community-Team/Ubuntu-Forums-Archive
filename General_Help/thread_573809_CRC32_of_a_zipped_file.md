---
title: "CRC32 of a zipped file?"
date: 2007-10-12
forum: General Help
---

### Post by Githlar on 2007-10-12
Is there any quick way to get the CRC32 of a file inside an archive (a standard zip archive)? I want to probe the archive file for its file list and somehow get the CRC32 of the file inside the archive (I'm trying to do this from a shell script)? When I was using Windows, WinRAR would do this for you and it was a handy feature.

I know a CRC32 can be generated with cksfv, but it can't get the CRC32 of a file inside of an archive without extracting it first.

---

### Post by Jussi Kukkonen on 2007-10-12
> it can't get the CRC32 of a file inside of an archive without extracting it first.
This is just a fact of life... Winrar may have done this automatically for you but it too would have had to extract the file first.

---

### Post by Githlar on 2007-10-12
No, when you open the archive, it shows the CRC32 next to the file entry without having to extract it first.

I'm a C/C++ programmer, so if somebody knows a way to do it that way, that would work too.

---

### Post by Jussi Kukkonen on 2007-10-12
> No, when you open the archive, it shows the CRC32 next to the file entry without having to extract it firs
In that case the crc is saved in the zip before data is compressed. I checked unzip man-pages and this is indeed the case. You should be able to print the CRC or check it, see *man unzip*.

---

