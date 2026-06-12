---
title: "Copy Flac Genre Tag to MP3 ID3 tag"
date: 2013-05-12
forum: General Help
---

### Post by bonelifer on 2013-05-12
I rip my CD's to FLAC and also convert those to MP3's for devices I have that need MP3.  I have one album that is Various Artists from various genres with 4 CD's. When I first ripped I didn't think to set the Genre for each track. I've updated the FLAC but would rather not try and manually copy that if I can get a bash script(in case this happens again).

Identical folder structure, and identical filenames. I just want to get the GENRE from the FLAC file and copy it to the Genre tag in the MP3.

---

### Post by scbingham on 2013-05-13
I use Sound Converter, which is available from the Software Centre to convert music files to mp3 and it copies the tags over too.

---

### Post by bonelifer on 2013-05-13
Yeah, these didn't have the genre when ripped. I'm trying to find a script to copy them from the FLAC(that I've since added the genre for each track).  The info wasn't available when converted being a various artist cd, the person that added that info to the freedb couldn't do a track by track genre.  I'm just looking to see if anyone knows of a way to automatically do this via a bash script.

---

### Post by scbingham on 2013-05-14
I understand the problem now. A quick google, I found this: 
[http://www.techrepublic.com/blog/opensource/how-to-tag-all-your-audio-files-in-the-fastest-possible-way/3444](http://www.techrepublic.com/blog/opensource/how-to-tag-all-your-audio-files-in-the-fastest-possible-way/3444)

Which uses id3tag in a bash script, which leads us to here:
[http://manpages.ubuntu.com/manpages/hardy/man1/id3tag.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/id3tag.1.html)

Good luck.

---

### Post by scbingham on 2013-05-14
And here is a link to a list of genre types & their corresponding numbers:
[http://axon.cs.byu.edu/~adam/gatheredinfo/organizedtables/musicgenrelist.php](http://axon.cs.byu.edu/~adam/gatheredinfo/organizedtables/musicgenrelist.php)

---

