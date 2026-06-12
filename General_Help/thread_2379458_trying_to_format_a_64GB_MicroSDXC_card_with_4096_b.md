---
title: "trying to format a 64GB MicroSDXC card with 4096 bytes per sector"
date: 2017-12-05
forum: General Help
---

### Post by ray field on 2017-12-05
I'm trying to flash Rockbox onto an xDuoo digital music player, and the micro SD card has to be formatted FAT32 with 4096 bytes per sector. I've come across conflicting reports for mkdosfs parameters, can someone help me (stabs in the dark have not worked yet)?

---

### Post by Kirk Schnable on 2017-12-06
When it comes to this sort of thing, I usually consult the man pages first: [https://linux.die.net/man/8/mkdosfs](https://linux.die.net/man/8/mkdosfs)

Did you try:
**mkdosfs -S 4096**

---

### Post by ray field on 2017-12-06
> **Kirk Schnable said:**
> When it comes to this sort of thing, I usually consult the man pages first: [https://linux.die.net/man/8/mkdosfs](https://linux.die.net/man/8/mkdosfs)

Did you try:
**mkdosfs -S 4096**

thanks. the man page usually does the trick for me, the problem here was I don't really understand cluster size (and it's one of those things I really don't want to). I believe your answer is correct, however for the record, someone on askubuntu.com suggested 
```

sudo mkfs.fat -S 4096 /dev/sdxn
```

as it happens, this wasn't enough to get Rockbox running -- it's a little mysterious exactly what sector size works -- an old 32GB card seems to have worked.

---

### Post by Kirk Schnable on 2017-12-06
Well, I don't really have any familiarity with Rockbox, but it's worth noting that at one time FAT32 did have a 32GB limitation.
[https://technet.microsoft.com/en-us/library/cc938432.aspx?f=255&MSPPError=-2147217396](https://technet.microsoft.com/en-us/library/cc938432.aspx?f=255&MSPPError=-2147217396)

It's possible that your specific use case needed a volume within that limitation to function properly.

---

### Post by ray field on 2017-12-08
There seems to be something else involved with the Xduoo X3 player recognizing the card. I tried a dozen times using the card formatted under Linux without success -- finally, I used the method recommended by Windows users, a formatting utility called "guiformat.exe," under my old VirtualBox XP installation, and it worked.

---

### Post by sudodus on 2017-12-08
Please share your solution also (at your question) at AskUbuntu :-)

Edit: Thanks, I think your solution will be available for more people now.

---

