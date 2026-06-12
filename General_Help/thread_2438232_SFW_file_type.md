---
title: "SFW file type"
date: 2020-03-07
forum: General Help
---

### Post by jgwphd on 2020-03-07
Does anyone know of a utility that can read old Seattle File Works file types? (file-name.SFW). I have some old 3.5' floppy disks with family pictures from 1997 and I need some kind of utility that can read this SFW file type (and hopefully allow me to save my old pictures in a modern format). Thanks for any suggestions.    Many Thanks  John

---

### Post by DuckHook on 2020-03-07
Websearching returns these links:

[https://file.org/extension/sfw](https://file.org/extension/sfw)
[https://www.computing.net/answers/mac/how-to-convert-seattle-filmwork-cds-to-a-jpeg-format/14603.html](https://www.computing.net/answers/mac/how-to-convert-seattle-filmwork-cds-to-a-jpeg-format/14603.html)

They all involve running Windows apps. You may be able to run such apps with WINE, but why not just load them on Windows (borrow a friend's machine if necessary), convert them to a more universal format (like jpeg or tiff) and not look back? FWIW, this is why I still have an old, rarely used Windows install kicking around in a VM.

---

### Post by DuckHook on 2020-03-07
UPDATE:

One of the recommendations in the above thread was for this app: [https://www.xnview.com/en/xnconvert/#downloads](https://www.xnview.com/en/xnconvert/#downloads)

****CAUTION****
I have no experience whatsoever with this app. It is purely the result of a web search. Use at your own risk. It involves the downloading of a third-party app from an unknown developer through an unknown website&#8212;all practices that I consider foolish&#8212;and so typically Windows-like. The tiny saving grace is that it has a native Linux version. Do your research on this vendor's dependability/integrity/competence. The usual cautions apply.

I recommend that you run it jailed in a VM, get your photos converted, then nuke it from orbit by rolling back to a pristine VM snapshot.

---

### Post by jgwphd on 2020-03-07
Wow!!!  .... anyone else?  I can't believe there is a file format the Linux world doesn't cover (open and read and convert). I swore off windows a long long time ago. I guess I'll keep looking. If anyone knows of anything please post a response. Many Thanks!

---

### Post by DuckHook on 2020-03-07
> **jgwphd said:**
> Wow!!!  .... anyone else?  I can't believe there is a file format the Linux world doesn't cover (open and read and convert). I swore off windows a long long time ago. I guess I'll keep looking. If anyone knows of anything please post a response. Many Thanks!

> **DuckHook said:**
> …I recommend that you run it jailed in a VM, get your photos converted, then nuke it from orbit by rolling back to a pristine VM snapshot.
I don't want to scare you off this app unnecessarily, especially when it looks like it could do the job for you. As helpers on this forum, we sometimes have to download and run apps that we know nothing about. When this is required, I use the method already referenced and requoted above: spin up a VM, download/install the app, run it while it is jailed within the VM, then roll back the VM to a clean snapshot afterwards. At the completion of this process, it's as if the download never happened. Provided you don't let your VMs access your LAN, there's not much real risk.

---

### Post by dragonfly41 on 2020-03-08
I have never used SFW (certainly used SWF) but [according to here]("http://fileformats.archiveteam.org/wiki/Seattle_FilmWorks") .. ImageMagick installed in Ubuntu can convert.

[http://fileformats.archiveteam.org/wiki/ImageMagick](http://fileformats.archiveteam.org/wiki/ImageMagick)

---

### Post by him610 on 2020-03-08
+ Post #6 
I believe I converted some SFW images a few years ago using imagemagick.

---

### Post by jgwphd on 2020-03-08
Ok, I'll try "imagemagik"  

A second question ...BTW, can anyone recommend any hardware that can read old 3.5" floppies. I do have a USB floppy drive reader I bought approx 15 years ago but I am only able to read 14 out of 37 disks. I get an error message on most of them saying "Error mounting /dev/sdb at media/...  : can't read superblock on dev/sdb"    I assume it might be a low signal level since the disks are over 20 years old and maybe ther is more sensitive USB reader that someone can recommend.

---

### Post by CelticWarrior on 2020-03-08
From what I've been learning in retrocomputing channels in Youtube - not personal experience - the USB flopply drives only read/write late high-density 1.44MB diskettes. If the ones giving errors aren't then that's the reason.

But the most likely cause is diskette failure due to old age. Especially if those are from the last leg of the format. According to the "8-bit guy", diskettes manufactured in the late 90s or newer are pure rubbish.

---

### Post by jgwphd on 2020-03-08
I can't tell when the disks were manufactured, but the label on them indicates the picture files were created with the ".SFW" file extensions in October 1997. Isn't there some kind of "more sensitive" diskette reader that might help?      

...or is there possibly some kind of software solution that might recover the picture files without any "official mounting" taking place.

---

### Post by CelticWarrior on 2020-03-08
No and no...

If you can find a still functional internal diskette drive and a motherboard supporting it then then that covers the possibility I've mentioned above. But it won't recover damaged diskettes, obviously. I/O errors means either not compatible or failled, unrecoverable, period.

---

### Post by dragonfly41 on 2020-03-08
Out of curiosity (since I still have some very old 8 inch floppies) I searched around.

[https://www.youtube.com/watch?v=q5MkWtQwx-s](https://www.youtube.com/watch?v=q5MkWtQwx-s)

You could look around for a local computer museum.

I still have a very old Compaq laptop in a shed.

---

### Post by him610 on 2020-03-08
Two cents worth....
Cleaned out my basement recently. Donated to Goodwill: one each Iomega Zip drive, several 100MB and 250MB disks for Zip drive; several mint-like 3.5 inch diskettes. Gave away the 3.5 inch disk drive a couple of years ago. 
Built a new system last month without CD/DVD RW drive; although, I still have one in an older system. Nothing lasts forever; progress continues relentlessly; the bits on magnetic media will fade eventually.
It is time for the obsolete hardware to go after backing up files worth keeping.

---

### Post by jgwphd on 2020-03-08
MANY MANY MANY THANKS!!!!    "Imagemagick" does what I want!         [https://imagemagick.org/script/install-source.php](https://imagemagick.org/script/install-source.php)      ...and NO WINDOWS!!!!!!   WHOO HOO!!!

---

### Post by jgwphd on 2020-03-08
According to expert on this video [https://www.youtube.com/watch?v=q5MkWtQwx-s](https://www.youtube.com/watch?v=q5MkWtQwx-s) that dragonfly41 posted: The magnetic media lasts a very long time and can be recovered????  ....I am thinking he must be referring to some way to read the diskettes with out actually mounting or opening them. The diskettes are pristine and there is NO damage. They have been sitting in an inside the home closet for probably 20 years. I am using [https://www.amazon.com/Teac-Corp-Floppy-Drive-External/dp/B0007VE044](https://www.amazon.com/Teac-Corp-Floppy-Drive-External/dp/B0007VE044). Does anyone have any suggestions?

---

### Post by dragonfly41 on 2020-03-08
[COLOR=#000000]Follow up the clues ..

[/COLOR][COLOR=#000000]Presenter: David Pogue NY Times Tech Columnist[/COLOR]

[https://www.nytimes.com/by/david-pogue](https://www.nytimes.com/by/david-pogue)

[https://davidpogue.com/](https://davidpogue.com/)

[https://davidpogue.com/contact/](https://davidpogue.com/contact/)

[COLOR=#000000]Ask how to contact Bob Daly.[/COLOR]

---

### Post by jgwphd on 2020-03-08
I have ordered another 1.44 floppy reader from another manufacturer to try that. Also, I seem to remember an Ubuntu program I ran from the terminal that would scan any media and recover files. I remember using it to recover pictures on an old camera and usb drive. But it was five/ten years ago but I can't remember what I did and the program name. Does anyone have any suggestions along that line of thinking?  Thanks!

---

### Post by dragonfly41 on 2020-03-08
photorec and testdisk?

---

### Post by jgwphd on 2020-03-08
Thanks!   I very much appreciate the discussion and all the assistance.  You guys are awesome!!!!!!!

---

