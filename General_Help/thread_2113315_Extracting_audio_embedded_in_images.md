---
title: "Extracting audio embedded in images"
date: 2013-02-07
forum: General Help
---

### Post by Stonecold1995 on 2013-02-07
On the imageboard 4chan, sometimes we have threads where we share music and other audio that's been embedded in image files.  The method of embedding sounds is this:
```
echo '[tag]' >> image.jpg
cat audio.ogg >> image.jpg
```
So the format is (with \n being newlines):
**|<---image-data--->\n<-[tag]->\n<---audio-data--->|**
It can also contain multiple audio files by repeating
**\n<-[tag]->\n<---audio-data--->**
for as many extra OGG files there are to embed (respecting the total size limit of 3 MB).

After that the file is masked using JavaScript with [this website]("http://cornarx.6te.net/mask.html") so they can bypass the embedded archive filter, which searches for the string "libVorbis".  For example, [this image]("http://www.pictureshack.us/images/78686_U_N_Owen_is_dead-original.jpg") contains unmasked embedded audio, and [this one]("http://www.pictureshack.us/images/31531_U_N_Owen_is_dead-masked.jpg") contains masked embedded audio.  The mask is reversible, however I don't know how to extract the audio that is embedded in the image.  Is there a way I can extract the audio via command line?  All I have to do is extract everything past "[tag]", but before the next tag, if it is present.


How do I extract the audio from the image files, assuming I know the tag's name?

---

### Post by Stonecold1995 on 2013-02-11
bump

---

### Post by Stonecold1995 on 2013-03-24
bump?

---

### Post by Impavidus on 2013-03-25
So you're trying to circumvent someones file format policy? Helping you with that could be against forum policy, which is probably the reason why nobody has responded.

Anyway, without being very specific, I would probably write a 15 line C code that could do exactly what you described in less time than it would take me to ask this forum for help three times. Of course assuming that the chance of your \n[tag]\n occuring in random data is negligible.

---

### Post by Stonecold1995 on 2013-03-25
> **Impavidus said:**
> So you're trying to circumvent someones file format policy? Helping you with that could be against forum policy, which is probably the reason why nobody has responded.
Embedded files are automatically blocked by the filter to prevent upload of malware (4chan.js) or child pornography (sinks).  Embedding Audio data is fine and legal, and the moderators of the site aren't too worried about embedded audio.  It is just easier for the admin of the site to allow us to moderate or own boards than it is for him to go to the trouble of modifying the filter.

> **Impavidus said:**
> Anyway, without being very specific, I would probably write a 15 line C code that could do exactly what you described in less time than it would take me to ask this forum for help three times. Of course assuming that the chance of your \n[tag]\n occuring in random data is negligible.
That's not much help considering I don't know much C, certainly not enough to do this at least.  And yes, the chance that the tag will occur in random data is less than 1 in 40 million chance (for a 5 letter tag, assuming I'm remembering my math), so negligible.

Because I am unable to program in C, could you suggest some utility that can be used in a bash script?  Perhaps something like tr (could it do this kind of thing?), or maybe cut?

---

