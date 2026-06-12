---
title: "&quot;Save Image As...&quot; failing in Firefox"
date: 2007-01-31
forum: General Help
---

### Post by roncrump on 2007-01-31
Hi,

I am having difficulty saving images from firefox. The same problem
seems to occur from a variety of sites, but as an illustration if I
have the image [http://ubuntuforums.org/gallery/showfull.php?photo=4523]("http://ubuntuforums.org/gallery/showfull.php?photo=4523")
open (a very nice background image option, IMHO), then right-click on it
and select Save Image As..., then I get a dialog prompting me to choose
what to save it as and where to.

Fine, except that the file does not appear in the selected directory, or
anywhere else for that matter (at least not under the expected name
- ```
sudo find / -name "*GhostFog*" -print
```  doesn't find anything).

My HD is nowhere near full (about 17%, 22Gb still available).

I can edit and create files in general, so I do not think it is a permissions issue (unless
somehow firefox has different (ie lower) permissions from the user that is using it).

Any suggestions welcome. I am running Edgy Eft (Update Manager says I'm up to date)
and firefox 2.0.0.1.

Thanks,
Ron

---

### Post by raul_ on 2007-01-31
Just try saving it with the default name, to the desktop folder, just for testing. Then 

```

ls ~/Desktop

```

---

### Post by roncrump on 2007-01-31
> **raul_ said:**
> Just try saving it with the default name, to the desktop folder, just for testing. Then 

```

ls ~/Desktop

```

Tried that - no joy.

It will let me set an image as a background from firefox (which results in it being saved
as Firefox-wallpaper.png, which kind of indicates it isn't a firefox permission problem),
but it won't let me actually choose to save it myself. Weird.

Ron.

---

### Post by raul_ on 2007-01-31
What do you mean with no joy? It didn't pop up, or the command didn't work? Sometimes Firefox saves images as "download.php" or something. Remember that when you change the name you can't rename it to "xpto", you have to rename it to "xpto.png"

---

### Post by roncrump on 2007-01-31
> **raul_ said:**
> What do you mean with no joy?

Sorry - I meant that nothing happened - the file was not saved to the Desktop
under any name (my Desktop is empty).

I appear to be having a general downloading problem from firefox: I just had reason
to try to download a PDF, and this also did not work (using save link as, also
just by clicking on it) - in both cases I get asked if I want to save the file to disk,
I say OK and nothing happens - no download dialog and no download.

In my firefox preferences the default download directory is set as the Desktop,
but this is not showing if I open the Download dialog using ctrl-y.

Ron.

---

### Post by ewankho on 2007-01-31
From the download window (Tools->Download) can you click on open to see if it opens? Also, you can try to right click on the file from the Download window and select 'Open containing folder.'

---

### Post by roncrump on 2007-01-31
> **ewankho said:**
> From the download window (Tools->Download) can you click on open to see if it opens? Also, you can try to right click on the file from the Download window and select 'Open containing folder.'

Not an option - nothing is appearing in the download window, which given that
nothing is downloading is probably not a surprise.

Ron.

---

### Post by raul_ on 2007-01-31
I'm sure this maybe a little "boring" but could you try with epiphany, and see if you could download it?

```

sudo aptitude install epiphany

```

If it does, maybe you have a corrupt Firefox profile. I suppose you have been able to download before.

---

### Post by roncrump on 2007-02-01
```

sudo aptitude install epiphany-browser

```

From epiphany I can save images. So how do I reset my Firefox profile?
backup .mozilla, delete the original and let it re-create everything?

Ron.

---

### Post by raul_ on 2007-02-01
Sorry for the typo.

Exactly.

---

### Post by roncrump on 2007-02-01
> **raul_ said:**
> Sorry for the typo.

Exactly.

That seems to have fixed it. Thanks for the help.

Ron.

---

### Post by mattmosher.com on 2007-02-08
why dont you just go to my site where my photo ghostfog is available for download.

[http://interfacelift.com/wallpaper/details.php?id=663](http://interfacelift.com/wallpaper/details.php?id=663)

---

### Post by roncrump on 2007-02-08
> **mattmosher.com said:**
> why dont you just go to my site where my photo ghostfog is available for download.

[http://interfacelift.com/wallpaper/details.php?id=663](http://interfacelift.com/wallpaper/details.php?id=663)

Cool. Now I can have it without the "Ubuntu Edgy Eft" bit. Which I like,
but makes it redundant in April (which I don't like as I don't change wallpapers
very often).

Thanks.

---

### Post by _simon_ on 2007-02-09
The image linked to in the first post has now been removed as I did not seek appropriate permission to have it hosted by Ubuntu forums.

I apologise publicly to mattmosher.com

---

