---
title: "ogg to flac to ogg again"
date: 2013-02-04
forum: General Help
---

### Post by CaptainMark on 2013-02-04
If I convert a music file from .ogg to .flac and then back to .ogg will there be an overall loss of quality between the original .ogg and the newer .ogg or will the quality remain the same?

I'm inclined to hope that because the .ogg is the lesser quality format anyway that it wont get any lower but I'm assuming the conversion wont do it any good either

---

### Post by Cheesemill on 2013-02-04
You will lose quality.

---

### Post by Yellow Pasque on 2013-02-04
You're certainly not going to magically gain audio quality, so why would you want to do this? If you're trying to make the file smaller and use a lower bitrate, then you're definitely going to lose quality.

---

### Post by CaptainMark on 2013-02-04
I'm only trying to strip the embedded album art to save on space, I can't find a way to remove embedded album art from .ogg but I can from .flac hence the conversion to one to the other and back again after stripping the artwork. to confirm I mean the album art embedded into the file not just the one associated with the album in my music database, I wasn't expecting to gain quality just hoping not to lose it, I've only a handful of albums that I wasn't able to re-rip from my cd's anyway so its not really much of a problem, I just like everything to be the same

---

### Post by Yellow Pasque on 2013-02-04
You should be able to do that with vorbiscomment command (in vorbis-tolls package):

```
       To just see what comment tags are in a file:

           vorbiscomment -l file.ogg

       To edit those comments:

           vorbiscomment -l file.ogg > file.txt
           [edit the comments in file.txt to your satisfaction]
           vorbiscomment -w -c file.txt file.ogg newfile.ogg
```

---

### Post by andrew.46 on 2013-02-04
If you follow temujin's suggestion you would simply need to strip the metatag *metadata_block_picture* and associated information from the file:

```

andrew@skamandros~/media/audio_cds/Beethoven Symphony No. 9 Chorale$ vorbiscomment -l test.ogg
album=Beethoven Symphony No. 9 "Chorale"
artist=Berliner Philharmoniker - Herbert von Karajan
title=Symphony No. 9 in D minor, Op. 125: I. Allegro ma non troppo, un poco maestoso
cddb=550fb505
genre=Classical
date=1963
tracknumber=01
**[COLOR="Red"]metadata_block_picture=[/COLOR]**AAAAAwAAAAppbWFnZS9qcGVnAAAAC0FsYnVtIENvdmVyAA [...]

```

I have omitted the albumart info as it is quite lengthy but you get the idea. A bit of handy sed work would remove this quite neatly...

---

### Post by Laobi on 2013-02-04
If you prefer GUI tools you can do that with EasyTAG.

It will not recompress the stream, just remove the album art, so you will not lose quality.

---

### Post by CaptainMark on 2013-02-05
I have easytag, it doesn't recognise embedded art for ogg, I will try vorbis comment tonight and check back

EDIT: Vorbiscomment works perfectly, thanks guys, I'll work on the sed line for it later, failing that its only a few albums left it wouldn't be the end of the world to do it manually for these ones

Many Thanks

---

### Post by Laobi on 2013-02-05
> **CaptainMark said:**
> I have easytag, it doesn't recognise embedded art for ogg

Sorry :( 
It did work when I tried it, but I tried it only with the .ogg files that had the album art added using EasyTAG too. I guess then it probably has problems recognizing the album art that was added using something else.

---

### Post by CaptainMark on 2013-02-05
Well thanks for the tips guys, I figured I'd post my solution here for anyone who would be so inclined to do the same thing in the future.
You can run the following from any folder you want to remove album art from, it's not recursive but feel free to change it if you want to, also it creates a backup folder just in case of mistakes so will promptly exit if another backup folder is present```
#!/bin/bash

# a simple script for removing album art from .ogg files
# depends on the vorbistools package

mkdir backup || exit

for song in ./*.ogg ; do
        mv "$song" "backup/$song"
        vorbiscomment -l "backup/$song" | sed  '/^METADATA_BLOCK_PICTURE/D' > comment.txt
        vorbiscomment -w -c comment.txt "backup/$song" "$song"
        rm comment.txt
done


```The mundane comments are only for my own reference if I need to come back to this in the future.

Regards

---

