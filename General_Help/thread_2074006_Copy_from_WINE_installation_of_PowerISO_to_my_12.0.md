---
title: "Copy from WINE installation of PowerISO to my 12.04"
date: 2012-10-20
forum: General Help
---

### Post by lemonoid on 2012-10-20
Okay so, I'm having some issues converting a .daa to .iso. I have PowerISO for linux installed, and that usually works when converting a .daa to .iso, however it keeps hanging at 59%. I'm not sure why. So I booted up WINE and installed PowerISO trial version there, because my Windows isn't currently working, I can't access my full installation of PowerISO. I'm trying to reinstall my windows but I'm missing my disc, and I had the iso, and PowerISO for some reason had converted it to a .daa extension. So when I have to convert to iso to re-install my Windows 7, using the trial version of PowerISO, you can't convert files over 350mb, the file is 3.1GB. So what I'm trying to do is take the files inside the .daa from WINE, and copy over into Linux, and make an iso from there. It allows me to copy to clipboard in WINE, but I can't access the clipboard in Linux. Does anyone know how to get files from the WINE clipboard to Ubuntu 12.04? ...or, does anyone have any idea of another successful way to convert from daa to iso in Ubuntu? I wouldn't worry about fixing my Windows, but my girlfriend really needs it for some programs she has to use for some of her classes.

---

### Post by Lisiano on 2012-10-20
There is a Linux tool to convert from .daa to .iso
Open up a terminal (Ctrl+Alt+T) and type in the following
```
sudo apt-get install daa2iso
```
Now just type in the following to convert from .daa to .iso
```
daa2iso file.daa file.iso
```

---

### Post by lemonoid on 2012-10-21
well. I copied the .daa to another computer with windows and tried the windows version of daa2iso. it got to around 30% the first time and then opted out with an error, the second time it got maybe to 12% then ended with an error as well. This is the error:

Error: the compressed INFLATE input is wrong or incomplete

I will try it on Ubuntu as well. I was looking for daa2iso earlier for Ubuntu but for some reason, all the download links I found were dead, I didn't think about using apt to get it. I'm beginning to wonder if somehow the file got corrupted during transfer. I got my brother to send it to me from my other computer, and he chose to send it through skype, which has actually worked pretty well. I am under the impression that poweriso uses .daa to make the file less corruptable, as it breaks it down into smaller chunks, but I don't like the concept. I wish it would've just stayed .iso.

EDIT
I just booted my Ubuntu back up and installed daa2iso, and it worked perfect the very first time. So, it may have been something to do with Windows using that program, idk why PowerISO wouldn't work on ubuntu though. Thanks.

---

### Post by Lisiano on 2012-10-21
.daa is a compressed format. If I understand it correctly, it has no redundancy, thus if a single block is corrupted in a .daa file, it will become unusable. .iso on the other hand will continue to work since it is basically an image of a disk. A file on the disk would get damaged but otherwise the iso is working.

Either way, glad I could help.

---

