---
title: "format of .lz4 files in /var/lib/apt/lists"
date: 2021-10-25
forum: General Help
---

### Post by Skaperen on 2021-10-25
there are a bunch of files in **[FONT=courier new]/var/lib/apt/lists[/FONT]**.  several, including the 4 largest files, have the **[FONT=courier new].lz4[/FONT]** extension.  i have tried to uncompress these files but everything i try with the xz, lzma, and unlzma commands tells me that the format is not recognized.  i am assuming they are in some raw format which requires knowing the custom filter chains that were used.  **does anyone know how to uncompress these files?**  i think they may be the ones that list all the files in all repository packages.  if so, those are the ones i need to have my script read.

---

### Post by Dennis N on 2021-10-25
> does anyone know how to uncompress these files?

lz4 command should do it.

```
 lz4  file.lz4 
```
would decompress the file.
```

dmn@Sydney:~$ apt-cache policy lz4
lz4:
  Installed: 1.9.2-2ubuntu0.20.04.1
  Candidate: 1.9.2-2ubuntu0.20.04.1
  Version table:
 *** 1.9.2-2ubuntu0.20.04.1 500

```

---

### Post by Skaperen on 2021-10-26
thank you very much.  i was not aware of that command or any others shown on its man page.  i should have, at lest, tried finding a man page for the extension.

---

