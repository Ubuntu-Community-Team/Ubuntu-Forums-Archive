---
title: "Looking for a utility to automatically rename my music files by their id3 tags"
date: 2007-01-04
forum: General Help
---

### Post by TeeAhr1 on 2007-01-04
I just bought an iAudio X5 (it's gorgeous, btw, I love it).  Unfortunately, I cannot sort by track number with it, it sorts everything alphabetically, which is a major pain for me.  I spent a long time tagging my music, and don't relish the thought of taking just as long renaming all the files.  Is there any sort of utility I can use that will look at my id3 tags and rename my files accordingly?  Thx...

-pete

---

### Post by kidders on 2007-01-04
Hi there,

There are lots and lots and *lots* of tools that can do things like this for you. You could try something like **apt-cache search id3|grep -i rename** or something similar, to find some in Ubuntu's repositories. Equally, Google should throw hundreds more at you. :-)

---

### Post by bonzodog on 2007-01-04
Install Quod Libet - it should come with Ex-Falso, which is an amazing utility that allows you to rename files based on the artist/title in the id3 tag. It also uses the mutagen system of assigning tags, which goes all the way to id3v2.4, and means they would be recognised  by almost any player available.

[http://www.sacredchao.net/quodlibet/wiki/Development/Mutagen](http://www.sacredchao.net/quodlibet/wiki/Development/Mutagen)

---

### Post by seelk on 2007-01-04
> **TeeAhr1 said:**
> I just bought an iAudio X5 (it's gorgeous, btw, I love it).  Unfortunately, I cannot sort by track number with it, it sorts everything alphabetically, which is a major pain for me.  I spent a long time tagging my music, and don't relish the thought of taking just as long renaming all the files.  Is there any sort of utility I can use that will look at my id3 tags and rename my files accordingly?  Thx...

-pete

I use [EasyTag]("http://easytag.sourceforge.net/").  You should be able to find it in the repositories.

---

### Post by Spano on 2007-01-04
I would suggest EasyTag as well, looked into this myself a couple of months ago and this is the app everyone seems to like.  Only thing is I could never figure out how to use it, documentations pretty thin.  Any tutorials out there?

---

### Post by justinjstark on 2007-01-04
> **Spano said:**
> I would suggest EasyTag as well, looked into this myself a couple of months ago and this is the app everyone seems to like.  Only thing is I could never figure out how to use it, documentations pretty thin.  Any tutorials out there?

I'm not sure about tutorials, but the basics are fairly simple.  You can just browse to the directory in which your music is located and change the id3 values manually for each song.  The little square buttons next to each field automatically assign the current value to all selected songs.

To automatically rename files, select the group of files that you would like to rename, go to scanner->rename files, select the directory and file format from the drop box, and press the scan selected files button which is the left-most button on the top.  Then just be sure to save the files and tags before closing.

---

### Post by strabes on 2007-01-04
I second the thought of using Ex Falso. It has a section where you can rename files based on their tags. I actually have an iAudio X5 coming in the mail today, and all my files are named with the track numbers first. Does this thing not have a database type function where it reads all the tags and then builds a library based on them? That kinda sux....

---

### Post by TeeAhr1 on 2007-01-04
(at the risk of threadjacking my own thread...)

Unfortunately no, it doesn't, which is stupid, because it does read id3 tags (it shows artist and title in the main screen).  I'm gonna hold out for a while and hope for a firmware update, but I'm also toying with the idea of installing [Rockbox]("http://www.rockbox.org/") (I'd just go ahead and do it, but putting non-official firmware on it voids the warranty).

---

### Post by TeeAhr1 on 2007-01-04
> **justinjstark said:**
> I'm not sure about tutorials, but the basics are fairly simple.  You can just browse to the directory in which your music is located and change the id3 values manually for each song.  The little square buttons next to each field automatically assign the current value to all selected songs.

To automatically rename files, select the group of files that you would like to rename, go to scanner->rename files, select the directory and file format from the drop box, and press the scan selected files button which is the left-most button on the top.  Then just be sure to save the files and tags before closing.

Hey, this is slick.  I'd played around a tiny bit with EasyTag before, but I didn't know it could do this.  Thx!

---

### Post by Falcorian on 2007-01-05
Although you seemed to have solved your problem, I'll add my 2 cents in case someone else has the same question.

Amarok has an option to do this built in: right click the song > Manage Files > Organize Files > Custom Format

---

### Post by 23meg on 2007-01-05
Audio Tag Tool does it nicely. It's in the repositories; the package name is *tagtool*.

---

### Post by bvanaerde on 2007-01-23
> **23meg said:**
> Audio Tag Tool does it nicely.
This one looks really promising, and it reminds me of Tag&Rename ;) 
It will come in handy now that I'm sorting out my music...

---

