---
title: "mp3 quality"
date: 2005-07-19
forum: General Help
---

### Post by Ferio on 2005-07-19
Is there any known way to change mp3 files from one bitrate to another? I mean, for instance, changing one mp3 file from 128 kbps to 320 kbps.

---

### Post by kori.mendocino on 2005-07-19
you can do so by converting them, but the only effect is going to be 3 times bigger files. the audio is already compressed in 128kbps and from this compressed file you will hardly ever recreate the quality which was lost during initial compression, which you want in order to compress them with better quality and et cetera. regression [e.g. from 320 to 128kbps] is possible, though

---

### Post by angkor on 2005-07-19
Nope, You can't add what's not there. 

If you encode a track to mp3 (e.g 192 kbps) it is compressed by removing things the 'average' human ear can't hear anyway. You can't add what has been removed. The only way is to re-encode it to a higher bitrate. I personally encode everything higher than 192kbps.

---

### Post by Ferio on 2005-07-20
Oh, yes, I know this, I was just asking about which software I could use to do it, in one way or the other, 'cos I have no idea about sound software :)

---

### Post by Ferio on 2005-07-20
No, I know the real quality will be the same and so, but I was asking if there is a possible way to do it; I remember some Win software calle something like "Power mp3 wma converter" that could do it, change the quality of a mp3 to a higher bitrate although the real effect were the same in the end.

BTW, really nice avatar.

---

### Post by doclivingston on 2005-07-20
You can't turn a lower bitrate mp3 into a higher one (192->320kbs in this case) - it can't recreate the information that isn't there.

You can turn high bitrate mp3s in lower ones (e.g. 320->192), but it will be worse quality than if you converted from the original to the lower bitrate - so you should reencode from the originals if possible. Ogg Vorbis is a special case for this, because you can convert from a high bitrate to a lower one and it will be identical to one that was encoded at the lower rate. This is called "peeling", but I'm not aware of any easy to use tools that let you do this.

Converting between formats (e.g. mp3 to ogg, or wma to mp3) does horrible things to the quality, so you should never do this unless you have to.

---

