---
title: "Nautilus Preview Only for &quot;Files smaller than...&quot; not working"
date: 2007-05-28
forum: General Help
---

### Post by panicb on 2007-05-28
currently using ubuntu Feisty..

in Nautilus, even if I set the preferences to not generate any thumbnails (preview) for
files bigger than 5mb, which is on my default, it still tries to grab thumbnails of huge videos,
causing a major slowdown when browsing through folders with many video files.

This applies to any type of preview-able files, such as flv and avi.

---

### Post by drs305 on 2007-05-28
You might try using gconf-editor to see if the change you are trying to make is sticking. I think the line you are looking for would be:

/apps/nautilus/preferences/thumbnail_limit

The default limit appears to be 5242880 bytes. If that doesn't solve your problem you could use the search feature of gconf-editor there are a few dozen references to ' thumbnailers ' and you might find one of those settings controls the byte size.

---

### Post by fragos on 2007-05-28
> **panicb said:**
> currently using ubuntu Feisty..

in Nautilus, even if I set the preferences to not generate any thumbnails (preview) for
files bigger than 5mb, which is on my default, it still tries to grab thumbnails of huge videos,
causing a major slowdown when browsing through folders with many video files.

This applies to any type of preview-able files, such as flv and avi.

It will only do this once because the thumbnails are saved.

---

### Post by ryanVickers on 2007-05-28
try setting it to not preview files other than images at all.  also, something must be setup wrong for that to significantly slow anything down!  Unless you've got a really old computer ;)

'course on windows, I had ~130 images in a folder, and the scrolling was just unbearable!  Not in Ubuntu, I have like 200 big video files in a folder, and quick as a whip!

---

### Post by wylfing on 2007-06-04
I just encountered a similar frustration. I work with large PostScript files all the time, and no matter what size limit I set under Preview preferences, it would always try to create a thumbnail. When you have a directory full of 50 MB PostScripts, your computer just became unusable for the next hour.

I fired up gconf-editor and looked under /desktop/gnome/thumbnailers. In there you can enable or disable various file types for thumbnailing. I switched PostScript completely off. It doesn't really do me any good to get thumbnails of those anyway -- they're all just on their way to becoming PDFs.

**@drs305** - FYI, the size preferences do seem to be saved properly under /apps/nautilus/preferences, but the file size isn't having any effect on actual behavior. I have it set at 500 KB and it's just being ignored.

Looks like this might be a confirmed bug dating back to at least Dapper: [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/40874](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/40874)

---

