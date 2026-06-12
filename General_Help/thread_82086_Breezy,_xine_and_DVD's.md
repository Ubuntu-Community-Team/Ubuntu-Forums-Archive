---
title: "Breezy, xine and DVD's"
date: 2005-10-25
forum: General Help
---

### Post by irv on 2005-10-25
One real problem that has me stumped is since upgrading to Breezy I can't play DVD's. I've tried unloading and reloading gxine, but everytime I try to play a DVD I get a "Read error from: Error reading NAV packet." and this is a gxine engine message.
I have notice that I have cdrom0 and cdrom1 in media but when I do an eject from cdrom0 or cdrom1, I see the same drive open which is my CD not my DVD. I also notice that movie clips from Netflix's website will not play using gxine. (Plug-in issue)
Once I put a DVD in the drive I can't eject it or un-mount it. The only way to get it out is by putting a pin in the small hole to release the DVD from the drive. Oh, I don't see the DVD drive in File System under media.(but maybe it is one of the cdrom's) Do you think Breezy had trouble seeing it? Under Disks Manager all I have listed is my two hard drives two CDRom's and a floppy which I do not have installed.I did some testing on the two CDRom's and when I put a DVD in the DVD Drive one of the CDRom's, which is dev "hdc" sees the Vidio disc, so I think it is seeing it. Also the xine program does start to play the DVD for a very short time and  then I get the error.

---

### Post by ecobuntu on 2005-10-26
do you have libdvdcss2?

---

### Post by thinkpadg41 on 2005-10-26
[QUOTE=irv]One real problem that has me stumped is since upgrading to Breezy I can't play DVD's. I've tried unloading and reloading gxine, but everytime I try to play a DVD I get a "Read error from: Error reading NAV packet." and this is a gxine engine message.
I have notice that I have cdrom0 and cdrom1 in media but when I do an eject from cdrom0 or cdrom1, I see the same drive open which is my CD not my DVD. I also notice that movie clips from Netflix's website will not play using gxine. (Plug-in issue)
Once I put a DVD in the drive I can't eject it or un-mount it. The only way to get it out is by putting a pin in the small hole to release the DVD from the drive. Oh, I don't see the DVD drive in File System under media.(but maybe it is one of the cdrom's) Do you think Breezy had trouble seeing it? Under Disks Manager all I have listed is my two hard drives two CDRom's and a floppy which I do not have installed.I did some testing on the two CDRom's and when I put a DVD in the DVD Drive one of the CDRom's, which is dev "hdc" sees the Vidio disc, so I think it is seeing it. Also the xine program does start to play the DVD for a very short time and  then I get the error.[/QUOTE]



....I had the same problems, fixed all with this Guide:

          [http://ubuntuguide.org/](http://ubuntuguide.org/)

---

