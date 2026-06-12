---
title: "Asking for Advice Re: Multiple Image Files"
date: 2008-06-30
forum: General Help
---

### Post by Anlace on 2008-06-30
Greetings All,

I'm looking for advice tonight with a interesting dilemma.  I hope that there is a program or process out there that can help with my project, and I hope that one or more of you can steer me in the right direction.

The quandary is this - I am helping a dear 84 year old friend move her data over from an old G4 onto a brand new MacMini.  The problem is the old version of iPhoto 2.0, and her lack of understanding, made a horrible mess out of the photos on the computer.  For my friend this is the primary reasons why she bothers with a computer at all, to email friends and family and share photos.

Between her lack of understanding and the abysmal way that iPhoto handled files, she has duplicates of almost everything and in many cases up to 6 copies of the same photo!  What a mess.  The entire collection of photos and images is in the neighborhood of 6,000 plus images.

Is there a program out there that can go through a directory and recursively compare file properties, particularly images, and find multiple copies?  This would have to work regardless of the file name.

Gwenview has a decent tool for that under Plugins > Collections > Find Duplicate Images . . . but it's not recursive. Is there a way to make the plugin work recursively?  I certainly didn't find anything in Configure Gwenview.

Are there any other options for finding multiple images recursively?

I eagerly await any and all helpful responses.

Thanks,
Gail

---

### Post by markekeller on 2008-07-01
Try [FDupes]("http://netdial.caribe.net/~adrian2/fdupes.html"), or if you prefer a graphical interface, [FSlint]("http://www.pixelbeat.org/fslint/") (the latter of which can clean other types of filesystem 'lint' besides duplicate files).  Both of those can search recursively.

If you want something specifically for images, there's [findimagedupes]("http://www.kudla.org/raindog/perl/"), too, though I don't think that one automatically deletes them for you.

And best of all, all three of these programs are in the Ubuntu repositories, so you can install them all with

```
sudo apt-get install fdupes fslint findimagedupes
```!

---

### Post by aysiu on 2008-07-01
I wouldn't recommend this for your friend, but you might find this useful in helping her:
[HOWTO: Remove duplicate files in a directory tree](http://ubuntuforums.org/showthread.php?t=647883)

---

### Post by Nemo_bis on 2010-01-01
See [Robust image duplicate finder](http://ubuntuforums.org/showpost.php?p=8594282&postcount=2): I found GQview to be the best tool.

---

