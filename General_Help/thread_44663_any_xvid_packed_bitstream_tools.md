---
title: "any xvid packed bitstream tools?"
date: 2005-06-27
forum: General Help
---

### Post by Sav on 2005-06-27
Hi, I'm searching for tools that remove the packed bitstream in xvid video files (divx stand-alone player compatibility).

I know that MP4Box does the work, but I have serious problems understanding its command line sintax.

Recent releases of avidemux2+ffmpeg may be usefull.

Could someone give me some tips about it?

Thanks

---

### Post by Sav on 2005-06-28
Up

---

### Post by flamarro on 2005-06-28
hi, avidemux2 does that very easy way, removes packed bitstream. Open avidemux, open your avi, it detects that the file has vop packed, asks you to unpack it, you say yes, then save it with outp. fmt saying avi unp vop and that's done.
Pay attention to what it says about the sound,

---

### Post by Sav on 2005-06-29
[QUOTE=flamarro]hi, avidemux2 does that very easy way, removes packed bitstream. Open avidemux, open your avi, it detects that the file has vop packed, asks you to unpack it, you say yes, then save it with outp. fmt saying avi unp vop and that's done.
Pay attention to what it says about the sound,[/QUOTE]

Thanks a lot.

I was scared, because I red in the official forum about a sort of a special script, that was bugged.
I'll try as soon as possible.
Bye

Sav

---

### Post by Sav on 2005-09-06
[QUOTE=flamarro]hi, avidemux2 does that very easy way, removes packed bitstream. Open avidemux, open your avi, it detects that the file has vop packed, asks you to unpack it, you say yes, then save it with outp. fmt saying avi unp vop and that's done.
Pay attention to what it says about the sound,[/QUOTE]

Thanks, it works  \\:D/

---

