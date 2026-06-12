---
title: "Alternative to pyrenamer: suggestions?"
date: 2019-10-15
forum: General Help
---

### Post by Paddy Landau on 2019-10-15
pyrenamer was a brilliant tool for bulk renaming of files, with back-references and previews. Unfortunately, it has been discontinued and doesn't work in 18.04. The nearest alternative that I've found is gprename, but it doesn't have back-references, which makes it unusable in some instances.

My latest requirement is to rename all files beginning with 8 digits to put dashes in them, for example:
[FONT=lucida console]20190930 rhubarb
20191015 blah blah[/FONT]
becomes
[FONT=&amp]2019-09-30 rhubarb[/FONT][FONT=lucida console]
2019-10-15 blah blah[/FONT]

Naturally, I will have other requirements in future, which is why I'm looking for a generic solution.

What alternatives to pyrenamer are there that are equally competent? I'll accept a terminal command as long as it has a "dry run" option to let me test before committing.

---

### Post by dragonfly41 on 2019-10-15
Sledgehammer to crack a nut idea .. if this is a frequent requirement and you prefer pyRenamer
Ubuntu 16.04 + pyRenamer in VirtualBox

Other than that idea, found this ..

[https://sourceforge.net/projects/file-folder-ren/](https://sourceforge.net/projects/file-folder-ren/)

---

### Post by uRock on 2019-10-15
I was broken hearted when I saw that pyrenamer had been removed from the repos. It was a great app. Nautilus now has the ability to do bulk renaming, but doesn't have the same options. According to[ this article]("https://www.ostechnix.com/how-to-rename-multiple-files-at-once-in-linux/"), Thunar has the ability to do mass renaming. It still isn't as good, but it works. I am not seeing anything in the default PCmanFM for bulk renaming.

The link I included also has some command line rename tools.

---

### Post by cruzer001 on 2019-10-15
I also was a user of pyrenamer.  For the quick fix I went with Thunar, but want something better.  I run Nemo, going to take a look there.

---

### Post by dragonfly41 on 2019-10-15
Perhaps the py extensions here might be developed further.
But I don't believe that they go as far as pyRenamer for batch replacement.

[https://www.giuspen.com/nautilus-pyextensions/](https://www.giuspen.com/nautilus-pyextensions/)

Developed by the author of CherryTree.

One thought is to combine this basic extension with an automation script
which runs through a directory of files to emulate pyRenamer functionality. 
I am an advocate of using toolchains.

---

### Post by Paddy Landau on 2019-10-17
> **dragonfly41 said:**
> Sledgehammer to crack a nut idea … Ubuntu 16.04 + pyRenamer in VirtualBox
Ha ha, yes, that's way over the top, especially on my old and slow computer!

> **dragonfly41 said:**
> found this … [https://sourceforge.net/projects/file-folder-ren/](https://sourceforge.net/projects/file-folder-ren/)
Thanks. That's not in the standard repositories, doesn't seem to have a PPA, and was last updated in 2015. So, I'll give that a miss!

> **uRock said:**
> According to[ this article]("https://www.ostechnix.com/how-to-rename-multiple-files-at-once-in-linux/")…
That article has a few highly useful command-line tools, which I think I shall use if I find nothing else. qmv looks good as well; using the VISUAL or EDITOR variable, I can use gedit or pluma or whatever and use their editing facilities.

> **dragonfly41 said:**
> Perhaps the py extensions here might be developed further…
Unfortunately, that goes way beyond my skill level!
______________________

Thank you everyone for your answers. I think that the command-line tools from @uRock will be my best bet. They're not as easy as pyrenamer, but they are as good for my purposes.

---

### Post by dragonfly41 on 2019-10-17
Late thought .. if you have a 16.04 LiveUSB somewhere you could install pyRenamer on that.
Beats the VirtualBox idea.

---

### Post by uRock on 2019-10-17
> **Paddy Landau said:**
> <snip>
Thank you everyone for your answers. I think that the command-line tools from @uRock will be my best bet. They're not as easy as pyrenamer, but they are as good for my purposes.

Drop by after a while and let us know which one ends up working the best for you.

---

